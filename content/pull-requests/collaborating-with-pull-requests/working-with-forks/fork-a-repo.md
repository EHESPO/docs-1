---
title: Fork a repository
allowTitleToDifferFromFilename: true
redirect_from:
  - /fork-a-repo
  - /forking
  - /articles/fork-a-repo
  - /github/getting-started-with-github/fork-a-repo
  - /github/getting-started-with-github/quickstart/fork-a-repo
  - /get-started/quickstart/fork-a-repo
intro: A fork is a new repository that shares code and visibility settings with the original upstream repository.
permissions: '{% data reusables.enterprise-accounts.emu-permission-fork %}'
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
category:
  - Work with forks
  - # Core LI.FI SDK & utilities
npm install @lifi/sdk viem

# For React apps (optional but recommended)
npm install @metamask/sdk-react @metamask/smart-accounts-kit-react

---
## About forks// lib/lifi-client.ts
import { createConfig, ChainId, getQuote, executeTransaction } from '@lifi/sdk';
import { createWalletClient, custom, http } from 'viem';
import { mainnet, arbitrum, optimism, polygon, base } from 'viem/chains';

// 1. Create the LI.FI SDK config
createConfig({
  integrator: 'EHEPS Green Data Centers', // Your dApp/company name[reference:4]
  apiKey: process.env.NEXT_PUBLIC_LIFI_API_KEY, // Get from portal.li.fi[reference:5]
});

// 2. Viem chain mapping (for chain verification)
export const CHAIN_MAP: Record<number, any> = {
  1: mainnet,
  42161: arbitrum,
  10: optimism,
  137: polygon,
  8453: base,
  // Add more chains as needed
};

// 3. Helper to get a viem chain from chain ID
export function getViemChain(chainId: number) {
  const chain = CHAIN_MAP[chainId];
  if (!chain) throw new Error(`Unsupported chain ID: ${chainId}`);
  return chain;
}. // components/WalletConnector.tsx
import { useSDK } from '@metamask/sdk-react';
import { createWalletClient, custom } from 'viem';
import { sepolia } from 'viem/chains';
import { useState } from 'react';

export function WalletConnector() {
  const { sdk, connected, connecting, account } = useSDK();
  const [walletClient, setWalletClient] = useState(null);

  const connect = async () => {
    try {
      await sdk?.connect();
      if (account) {
        // Create a viem wallet client from the MetaMask provider
        const client = createWalletClient({
          chain: sepolia,
          transport: custom(window.ethereum),
        });
        setWalletClient(client);
      }
    } catch (err) {
      console.error('Connection failed:', err);
    }
  };
  // lib/lifi-quote.ts
import { ChainId, getQuote } from '@lifi/sdk';

export async function getCrossChainQuote(params: {
  fromAddress: string;
  fromChain: number;
  toChain: number;
  fromToken: string;
  toToken: string;
  fromAmount: string;
}) {
  const quote = await getQuote({
    fromAddress: params.fromAddress,
    fromChain: params.fromChain,
    toChain: params.toChain,
    fromToken: params.fromToken,
    toToken: params.toToken,
    fromAmount: params.fromAmount,
  });

  return quote;
}

// Example usage:
// const quote = await getCrossChainQuote({
//   fromAddress: '0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045',
//   fromChain: ChainId.ARB,      // 42161
//   toChain: ChainId.OPT,        // 10
//   fromToken: '0x000...000',    // native token (ETH)
//   toToken: '0x000...000',      // native token (ETH)
//   fromAmount: '1000000000000000000', // 1 ETH in wei
// });

  return (
    <div>
      {!connected ? (
        <button onClick={connect}>Connect MetaMask</button>
      ) : (
        <div>
          <p>✅ Connected: {account}</p>
          {/* Smart Account will be available via context */}
        </div>
      )}
    </div>
  );
}.... 
// lib/lifi-execute.ts
import { getViemChain } from './lifi-client';
import { executeTransaction } from '@lifi/sdk';

// 4a. Ensure wallet is on the correct chain[reference:6]
export async function ensureCorrectChain(
  walletClient: any,
  targetChainId: number
) {
  const currentChainId = await walletClient.getChainId();
  if (currentChainId !== targetChainId) {
    console.log(`Switching from chain ${currentChainId} to ${targetChainId}`);
    await walletClient.switchChain({ id: targetChainId });
    // Verify switch succeeded
    const newChainId = await walletClient.getChainId();
    if (newChainId !== targetChainId) {
      throw new Error(`Failed to switch to chain ${targetChainId}`);
    }
  }
  return true;

 . 
}
// components/CrossChainSwap.tsx
import { useState } from 'react';
import { useSDK } from '@metamask/sdk-react';
import { getCrossChainQuote } from '../lib/lifi-quote';
import { executeCrossChainSwap } from '../lib/lifi-execute';
import { parseEther } from 'viem';

export function CrossChainSwap() {
  const { account } = useSDK();
  const [loading, setLoading] = useState(false);
  const [quote, setQuote] = useState(null);
  const [txHash, setTxHash] = useState('');
  const [error, setError] = useState('');

  const handleSwap = async () => {
    if (!account) {
      setError('Please connect your wallet first');
      return;
    }

    setLoading(true);
    setError('');
    setTxHash('');

    try {
      // 1. Get quote (Arbitrum → Optimism, 0.01 ETH)
      const quoteResult = await getCrossChainQuote({
        fromAddress: account,
        fromChain: 42161, // Arbitrum
        toChain: 10,      // Optimism
        fromToken: '0x0000000000000000000000000000000000000000',
        toToken: '0x0000000000000000000000000000000000000000',
        fromAmount: parseEther('0.01').toString(),
      });
      setQuote(quoteResult);

      // 2. Execute the swap
      // Note: In a real app, you'd get walletClient from context
      const walletClient = await getWalletClient(); // your viem client
      const result = await executeCrossChainSwap(
        walletClient,
        quoteResult,
        account
      );
      setTxHash(result.hash);
    } catch (err: any) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  };
import { createConfig } from '@lifi/sdk';

createConfig({
  integrator: 'EHEPS',
  eip7702: {
    enabled: true,
    // Optional: specify factory address if using a custom one
    factoryAddress: '0x...',
  },
});
  return (
    <div className="p-6 border rounded-xl">
      <h2 className="text-xl font-bold mb-4">🌉 Cross-Chain Swap</h2>
      <button
        onClick={handleSwap}
        disabled={loading || !account}
        className="bg-blue-600 text-white px-6 py-2 rounded disabled:opacity-50"
      >
        {loading ? 'Processing...' : 'Swap 0.01 ETH (Arb → Opt)'}
      </button>
      {txHash && (
        <p className="mt-3 text-green-600">
          ✅ Tx sent: <span className="font-mono text-sm">{txHash}</span>
        </p>
      )}
      {error && <p className="mt-3 text-red-600">❌ {error}</p>}
      {quote && (
        <details className="mt-4 text-sm">
          <summary>View Quote Details</summary>
          <pre className="bg-gray-100 p-3 rounded mt-2 overflow-auto max-h-60">
            {JSON.stringify(quote, null, 2)}
          </pre>
        </details>
      )}
    </div>
  );
}

// 4b. Build and send transaction[reference:7]
export async function executeCrossChainSwap(
  walletClient: any,
  quote: any,
  fromAddress: string
) {
  const txRequest = quote.transactionRequest;
  
  // Ensure correct chain
  await ensureCorrectChain(walletClient, txRequest.chainId);

  // Build the transaction
  const tx = {
    to: txRequest.to,
    data: txRequest.data,
    value: BigInt(txRequest.value || '0x0'),
    gas: BigInt(txRequest.gasLimit),
    chainId: txRequest.chainId,
  };

  // Send the transaction
  const hash = await walletClient.sendTransaction({
    account: fromAddress,
    to: tx.to as `0x${string}`,
    data: tx.data as `0x${string}`,
    value: tx.value,
    gas: tx.gas,
  });

  return { hash, txRequest };
}. // components/LifiWidget.tsx
import { LifiWidget, Theme } from '@lifi/widget';

export function LifiWidgetComponent() {
  return (
    <LifiWidget
      config={{
        integrator: 'EHEPS Green Data Centers',
        theme: Theme.Dark,
        containerStyle: { width: 400, height: 600 },
        // Optional: lock destination chain
        // destinationChain: 30, // Rootstock
      }}
    />
  );
}# .env.local
NEXT_PUBLIC_LIFI_API_KEY=your_lifi_api_key
NEXT_PUBLIC_INFURA_KEY=your_infura_key
NEXT_PUBLIC_METAMASK_SDK_VERSION=11.0.0


Resource Link
LI.FI SDK Docs docs.li.fi/sdk/overview
GitHub Repository github.com/lifinance/sdk
Transaction Execution Guide docs.li.fi/agents/workflows/execution
Five-Call API Recipe docs.li.fi/agents/quick-start/five-call-recipe
MetaMask Smart Accounts docs.metamask.io
{% data reusables.repositories.fork-definition-long %} For more information, see [AUTOTITLE](/pull-requests/collaborating-with-pull-requests/working-with-forks).

### Propose changes to someone else's project

For example, you can use forks to propose changes related to fixing a bug. Rather than logging an issue for a bug you have found, you can:

* Fork the repository.
* Make the fix.
* Submit a pull request to the project owner.

### Use someone else's project as a starting point for your own idea.

Open source software is based on the idea that by sharing code, we can make better, more reliable software. For more information, see the [About the Open Source Initiative](https://opensource.org/about) on the Open Source Initiative.

For more information about applying open source principles to your organization's development work on {% data variables.product.prodname_dotcom %}, see {% data variables.product.prodname_dotcom %}'s white paper [An introduction to innersource](https://resources.github.com/whitepapers/introduction-to-innersource/).

When creating your public repository from a fork of someone's project, make sure to include a license file that determines how you want your project to be shared with others. For more information, see [Choose an open source license](https://choosealicense.com/) at choosealicense.com.

{% data reusables.open-source.open-source-guide-repositories %} {% data reusables.open-source.open-source-learning %}

## Prerequisites

If you haven't yet, first set up Git and authentication with {% data variables.location.product_location %} from Git. For more information, see [AUTOTITLE](/get-started/git-basics/set-up-git).

## Forking a repository

{% webui %}

You might fork a project to propose changes to the upstream repository. In this case, it's good practice to regularly sync your fork with the upstream repository. To do this, you'll need to use Git on the command line. You can practice setting the upstream repository using the same [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) repository you just forked.

1. On {% ifversion fpt or ghec %}{% data variables.product.prodname_dotcom %}{% else %}{% data variables.location.product_location %}{% endif %}, navigate to the [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) repository.
1. In the top-right corner of the page, click **Fork**.

   ![Screenshot of the main page of repository. A button, labeled with a fork icon and "Fork 59.3k," is outlined in dark orange.](/assets/images/help/repository/fork-button.png)
1. Under "Owner," select the dropdown menu and click an owner for the forked repository.
1. By default, forks are named the same as their upstream repositories. Optionally, to further distinguish your fork, in the "Repository name" field, type a name.
1. Optionally, in the "Description" field, type a description of your fork.
1. Optionally, select **Copy the DEFAULT branch only**.

   For many forking scenarios, such as contributing to open-source projects, you only need to copy the default branch. If you do not select this option, all branches will be copied into the new fork.
1. Click **Create fork**.

> [!NOTE]
> If you want to copy additional branches from the upstream repository, you can do so from the **Branches** page. For more information, see [AUTOTITLE](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository).

{% endwebui %}

{% cli %}

{% data reusables.cli.cli-learn-more %}

To create a fork of a repository, use the `gh repo fork` subcommand.

```shell
gh repo fork REPOSITORY
```

To create the fork in an organization, use the `--org` flag.

```shell
gh repo fork REPOSITORY --org "octo-org"
```

{% endcli %}

{% desktop %}

You can fork a repository on {% data variables.product.prodname_dotcom_the_website %} or in {% data variables.product.prodname_desktop %}. For information about forking on {% data variables.product.prodname_dotcom_the_website %}, see [the web browser version of this article](/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo?tool=webui).

{% data reusables.desktop.forking-a-repo %}

{% enddesktop %}

{% webui %}

## Cloning your forked repository

Right now, you have a fork of the Spoon-Knife repository, but you do not have the files in that repository locally on your computer.

1. On {% ifversion fpt or ghec %}{% data variables.product.prodname_dotcom %}{% else %}{% data variables.location.product_location %}{% endif %}, navigate to **your fork** of the Spoon-Knife repository.
{% data reusables.repositories.copy-clone-url %}
{% data reusables.command_line.open_the_multi_os_terminal %}
{% data reusables.command_line.change-current-directory-clone %}
1. Type `git clone`, and then paste the URL you copied earlier. It will look like this, with your {% data variables.product.github %} username instead of `YOUR-USERNAME`:

   ```shell
   git clone https://{% data variables.product.product_url %}/YOUR-USERNAME/Spoon-Knife
   ```

1. Press **Enter**. Your local clone will be created.

   ```shell
   $ git clone https://{% data variables.product.product_url %}/YOUR-USERNAME/Spoon-Knife
   > Cloning into `Spoon-Knife`...
   > remote: Counting objects: 10, done.
   > remote: Compressing objects: 100% (8/8), done.
   > remote: Total 10 (delta 1), reused 10 (delta 1)
   > Unpacking objects: 100% (10/10), done.
   ```

{% endwebui %}

{% cli %}

## Cloning your forked repository

Right now, you have a fork of the Spoon-Knife repository, but you do not have the files in that repository locally on your computer.

{% data reusables.cli.cli-learn-more %}

To create a clone of your fork, use the `--clone` flag.

```shell
gh repo fork REPOSITORY --clone=true
```

{% endcli %}

## Configuring Git to sync your fork with the upstream repository

When you fork a project in order to propose changes to the upstream repository, you can configure Git to pull changes from the upstream repository into the local clone of your fork.

{% webui %}

1. On {% ifversion fpt or ghec %}{% data variables.product.prodname_dotcom %}{% else %}{% data variables.location.product_location %}{% endif %}, navigate to the [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) repository.
{% data reusables.repositories.copy-clone-url %}
{% data reusables.command_line.open_the_multi_os_terminal %}
1. Change directories to the location of the fork you cloned.
    * To go to your home directory, type just `cd` with no other text.
    * To list the files and folders in your current directory, type `ls`.
    * To go into one of your listed directories, type `cd YOUR-LISTED-DIRECTORY`.
    * To go up one directory, type `cd ..`.
1. Type `git remote -v` and press **Enter**. You will see the current configured remote repository for your fork.

   ```shell
   $ git remote -v
   > origin  https://{% data variables.product.product_url %}/YOUR-USERNAME/YOUR-FORK.git (fetch)
   > origin  https://{% data variables.product.product_url %}/YOUR-USERNAME/YOUR-FORK.git (push)
   ```

1. Type `git remote add upstream`, and then paste the URL you copied in Step 3 and press **Enter**. It will look like this:

   ```shell
   git remote add upstream https://{% data variables.product.product_url %}/ORIGINAL-OWNER/Spoon-Knife.git
   ```

1. To verify the new upstream repository you have specified for your fork, type `git remote -v` again. You should see the URL for your fork as `origin`, and the URL for the upstream repository as `upstream`.

   ```shell
   $ git remote -v
   > origin    https://{% data variables.product.product_url %}/YOUR-USERNAME/YOUR-FORK.git (fetch)
   > origin    https://{% data variables.product.product_url %}/YOUR-USERNAME/YOUR-FORK.git (push)
   > upstream  https://{% data variables.product.product_url %}/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git (fetch)
   > upstream  https://{% data variables.product.product_url %}/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git (push)
   ```

Now, you can keep your fork synced with the upstream repository with a few Git commands. For more information, see [AUTOTITLE](/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork).

{% endwebui %}

{% cli %}

{% data reusables.cli.cli-learn-more %}

To configure a remote repository for the forked repository, use the `--remote` flag.

```shell
gh repo fork REPOSITORY --remote=true
```

To specify the remote repository's name, use the `--remote-name` flag.

```shell
gh repo fork REPOSITORY --remote-name "main-remote-repo"
```

{% endcli %}

### Editing a fork

You can make any changes to a fork, including:

* **Creating branches:** [_Branches_](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository) allow you to build new features or test out ideas without putting your main project at risk.
* **Opening pull requests:** If you want to contribute back to the upstream repository, you can send a request to the original author to pull your fork into their repository by submitting a [pull request](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

## Find another repository to fork

Fork a repository to start contributing to a project. {% data reusables.repositories.you-can-fork %} For more information about when you can fork a repository, see [AUTOTITLE](/pull-requests/collaborating-with-pull-requests/working-with-forks/about-permissions-and-visibility-of-forks).

{% ifversion fpt or ghec %}You can browse [Explore {% data variables.product.prodname_dotcom %}](https://github.com/explore) to find projects and start contributing to open source repositories. For more information, see [AUTOTITLE](/get-started/exploring-projects-on-github/finding-ways-to-contribute-to-open-source-on-github).

{% endif %}

## Next steps

You have now forked a repository, practiced cloning your fork, and configured an upstream repository.

* For more information about cloning the fork and syncing the changes in a forked repository from your computer, see [AUTOTITLE](/get-started/git-basics/set-up-git).

* You can also create a new repository where you can put all your projects and share the code on {% data variables.product.prodname_dotcom %}. {% data reusables.getting-started.create-a-repository %}

* {% data reusables.getting-started.being-social %}

* {% data reusables.support.connect-in-the-forum-bootcamp %}
