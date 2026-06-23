---
title: What is GitHub Copilot?
intro: 'Learn what {% data variables.product.prodname_copilot_short %} is and what you can do with it.'
versions:
  feature: copilot
shortTitle: What is GitHub Copilot?
redirect_from:
  - /copilot/copilot-individual
  - /copilot/copilot-individual/about-github-copilot-individual
  - /copilot/copilot-business/about-github-copilot-business
  - /copilot/github-copilot-enterprise/about-github-copilot-enterprise
  - /copilot/github-copilot-enterprise/overview
  - /copilot/overview-of-github-copilot/about-github-copilot-for-individuals
  - /copilot/overview-of-github-copilot/about-github-copilot
  - /copilot/overview-of-github-copilot/about-github-copilot-individual
  - /copilot/overview-of-github-copilot/about-github-copilot-for-business
  - /copilot/overview-of-github-copilot/about-github-copilot-business
  - /copilot/github-copilot-enterprise/overview/about-github-copilot-enterprise
  - /copilot/configuring-github-copilot/configuring-github-copilot-settings-in-your-organization
  - /copilot/managing-copilot-business
  - /copilot/managing-copilot-for-business
  - /copilot/github-copilot-enterprise
  - /copilot/copilot-business
  - /copilot/about-github-copilot/what-is-github-copilot
contentType: get-started
category:
  - Learn about Copilot
---

{% data variables.product.prodname_copilot %} is an AI coding assistant that helps you write code faster and with less effort. Then, you can focus more energy on problem solving and collaboration.

Research shows that {% data variables.product.prodname_copilot_short %} increases developer productivity and accelerates software development. See [Research: quantifying {% data variables.product.prodname_copilot %}’s impact on developer productivity and happiness](https://github.blog/2022-09-07-research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/) in the {% data variables.product.prodname_dotcom %} blog.

## Features

You can use {% data variables.product.prodname_copilot_short %} to:

* Get code suggestions as you type in your IDE.
* Chat with {% data variables.product.prodname_copilot_short %} to get help with your code.
* Ask for help using the command line.
* Organize and share context with {% data variables.copilot.copilot_spaces %} to get more relevant answers.
* Generate descriptions of changes in a pull request.
* Research, plan, make code changes, and create pull requests for you to review. 

**For enterprises and organizations with data residency requirements:** If you use {% data variables.product.prodname_ghe_cloud %}, {% data variables.product.prodname_copilot_short %} can enforce geographic data residency. See [AUTOTITLE](/admin/data-residency/github-copilot-with-data-residency).

Use {% data variables.product.prodname_copilot_short %} in the following places:

* Your IDE
* {% data variables.product.prodname_mobile %}, as a chat interface
* {% data variables.product.prodname_windows_terminal %} Canary, through the Terminal Chat interface
* The command line, through the {% data variables.product.prodname_cli %}
* The {% data variables.product.github %} website

See [AUTOTITLE](/copilot/about-github-copilot/github-copilot-features).

## Get access

You can start using {% data variables.product.prodname_copilot_short %} in several ways, depending on your role and needs.

### Individuals

* **Try {% data variables.product.prodname_copilot_short %} for free.** Use {% data variables.copilot.copilot_free_short %} to explore core features with no paid plan required.
* **Subscribe to a paid plan.** Upgrade to {% data variables.copilot.copilot_pro_short %}, {% data variables.copilot.copilot_pro_plus_short %}, or {% data variables.copilot.copilot_max_short %} for access to premium features, increased access to models, and higher available monthly allowance of {% data variables.product.prodname_ai_credits_short %}.
* **Get free access if you're eligible.** Students, teachers, and open source maintainers may qualify for access to premium features at no cost. See [AUTOTITLE](/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students) and [AUTOTITLE](/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-teachers-and-os-maintainers).
* **Request access from your organization.** If your organization or enterprise has a {% data variables.product.prodname_copilot %} plan, you can request access by going to [https://github.com/settings/copilot](https://github.com/settings/copilot) and request access under "Get {% data variables.product.prodname_copilot_short %} from an organization."

See [AUTOTITLE](/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/getting-started-with-copilot-on-your-personal-account/getting-started-with-a-copilot-plan) for more information.

### Organizations and enterprises

>[!IMPORTANT]
> {% data reusables.copilot.plans.organization-plans-paused %}

**Organization owners** can get {% data variables.copilot.copilot_business_short %} for their team through an enterprise account. If you don't already have an enterprise account, you can create one specifically for managing {% data variables.copilot.copilot_business_short %} licenses. See [AUTOTITLE](/copilot/concepts/about-enterprise-accounts-for-copilot-business).

If your organization is owned by an enterprise that has a {% data variables.product.prodname_copilot_short %} subscription, you can ask your enterprise owner to enable {% data variables.product.prodname_copilot_short %} for your organization. Go to [https://github.com/settings/copilot](https://github.com/settings/copilot) and request access under "Get {% data variables.product.prodname_copilot_short %} from an organization."

**Enterprise owners** can set up {% data variables.copilot.copilot_business_short %} or {% data variables.copilot.copilot_enterprise_short %} for their enterprise by [contacting {% data variables.product.github %}'s Sales team](https://github.com/enterprise/contact?ref_product=copilot&ref_type=engagement&ref_style=text). 

## Next steps

* Learn more about {% data variables.product.prodname_copilot_short %} features. See [AUTOTITLE](/copilot/about-github-copilot/github-copilot-features).
* Start using {% data variables.product.prodname_copilot_short %}. See [AUTOTITLE](/copilot/setting-up-github-copilot).

## Further reading

* [Frequently asked questions](https://github.com/features/copilot#faq) about {% data variables.product.prodname_copilot %}
* [{% data variables.product.prodname_copilot %} Trust Center](https://copilot.github.trust.page/)
<?php
// ============================================================
// PRODUCT OFFERS PAGE – EHEPS ORGANIZATION (UPDATED)
// Added: GitHub, MCP, Atlassian (already present)
// ============================================================

// ------------------------------------------------------------
// CONFIGURATION
// ------------------------------------------------------------
$domains      = ['eheps.org', 'eheps.com'];
$owner_email  = 'ewaz.2010@gmail.com';
$super_admins = [
    'Executive@eheps.co'      => 'Super Admin',
    'Executivedirector@eheps.org' => 'Super Admin'
];

// ------------------------------------------------------------
// OFFERS DATA
// ------------------------------------------------------------
$top_tools = [
    ['name' => 'Adobe Express', 'desc' => 'Create and scale your impact for free on web and mobile.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Adobe Acrobat Pro', 'desc' => 'Save 94% on the essential document solution for nonprofits.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Claude', 'desc' => 'Elevate your nonprofit’s writing, research, and daily work with Claude AI at ~70% off.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Hootsuite', 'desc' => 'Optimize social media with 60% off Hootsuite.', 'btn' => 'Buy now', 'link' => '#'],
    ['name' => 'Microsoft 365 Business Premium', 'desc' => '75% off for eligible nonprofits.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Microsoft 365 Copilot', 'desc' => '15% discount for eligible nonprofits.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Microsoft Azure Grant', 'desc' => '$2,000 (USD) Azure services credits per year.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Microsoft Power Apps', 'desc' => 'Free for up to 10 users, $2.50/user/month after.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'monday.com', 'desc' => '10 free users and 70% off additional seats.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'OpenAI', 'desc' => 'ChatGPT Team at $8/user/month or up to 75% off Enterprise.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Zoom', 'desc' => '50% off Zoom for nonprofits.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Docusign', 'desc' => 'Up to 50% off IAM and 30% off eSignature.', 'btn' => 'Buy now', 'link' => '#'],
];

$expert_services = [
    ['name' => 'YouDoGood marketing', 'desc' => 'High-impact short-form video and expert social services.', 'btn' => 'Learn more', 'link' => '#']
];

$discounted_software = [
    ['name' => 'Adobe Acrobat Pro', 'desc' => 'Save 94% on the essential document solution.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Adobe Express', 'desc' => 'Create and scale your impact for free.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Asana', 'desc' => '50% off Asana’s work management tools.', 'btn' => 'Buy now', 'link' => '#'],
    ['name' => 'Atlassian', 'desc' => '75% off Jira, Confluence, and Trello for better work management.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Auth0', 'desc' => '50% off Auth0’s advanced security tools.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Bugle', 'desc' => 'Free volunteer management with Bugle’s Community Plan.', 'btn' => 'Get started free', 'link' => '#'],
    ['name' => 'Canva', 'desc' => 'Design high-impact marketing materials, 100% free.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Claude', 'desc' => 'Elevate writing and research with Claude AI at ~70% off.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Constant Contact', 'desc' => 'Up to 35% off marketing automation tools.', 'btn' => 'Start free trial', 'link' => '#'],
    ['name' => 'Docusign', 'desc' => 'Up to 50% off IAM and 30% off eSignature.', 'btn' => 'Buy now', 'link' => '#'],
    ['name' => 'Easy Board', 'desc' => '20% off board and committee management.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Eventbrite', 'desc' => '50% off Eventbrite’s premium ticketing.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'GitLab', 'desc' => 'Up to 20 free seats, plus discounts on additional seats.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Givebutter', 'desc' => 'Free all-in-one fundraising platform.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Google', 'desc' => '70%+ off Workspace and Ad Grants (Google for Nonprofits).', 'btn' => 'Apply', 'link' => 'https://www.google.com/nonprofits/'],
    ['name' => 'Keela', 'desc' => '10% off Keela’s nonprofit CRM with AI-powered tools.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'AI for Community training', 'desc' => 'Live instructor-led training on AI tools for nonprofits.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Goodstack Grants Pro', 'desc' => 'Discover grant opportunities with AI assistant Maia.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Gusto', 'desc' => 'First month free on online payroll and benefits.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Hootsuite', 'desc' => '60% off social media management.', 'btn' => 'Buy now', 'link' => '#'],
    ['name' => 'LinkedIn Fundraise', 'desc' => '75% off LinkedIn Sales Navigator Core.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Microsoft', 'desc' => 'Savings on Azure, Dynamics 365, and Microsoft 365.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Microsoft 365 Business Premium', 'desc' => '75% off for eligible nonprofits.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Microsoft 365 Copilot', 'desc' => '15% discount on AI assistant.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Microsoft Azure Grant', 'desc' => '$2,000 (USD) Azure credits per year.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Microsoft Power Apps', 'desc' => 'Free for 10 users, $2.50/month after.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'monday.com', 'desc' => '10 free users and 70% off additional seats.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'N2F', 'desc' => '20% off expense management solution.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'New Relic', 'desc' => '1,000 GB data and three free full-platform users.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'NordLayer', 'desc' => '40% off network security solutions.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Okta', 'desc' => '50% off secure identity solutions.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'OpenAI', 'desc' => 'ChatGPT Team at $8/user/month or up to 75% off Enterprise.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Sage', 'desc' => '50% off Sage Intacct accounting.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Splunk', 'desc' => 'Big data tools, free for nonprofits.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Twilio', 'desc' => '$100 credits and discounts on communications tools.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Workvivo', 'desc' => '50% off employee engagement platform.', 'btn' => 'Apply', 'link' => '#'],
    ['name' => 'Zoom', 'desc' => '50% off collaboration and communication solutions.', 'btn' => 'Apply', 'link' => '#'],
    // --- NEW ADDITIONS ---
    ['name' => 'GitHub', 'desc' => 'GitHub Global Campus for Nonprofits – free GitHub Team for eligible organizations, plus discounted GitHub Copilot for your development teams.', 'btn' => 'Apply', 'link' => 'https://github.com/nonprofit/'],
    ['name' => 'MCP (Model Context Protocol)', 'desc' => 'Leverage AI agent capabilities with MCP – enabling seamless integrations, data access, and advanced automation for your nonprofit projects and workflows.', 'btn' => 'Learn more', 'link' => '#'],
];

// Featured offers (Top of page)
$featured = [
    ['name' => 'Adobe Acrobat Pro', 'desc' => 'Save 94% on the essential document solution for nonprofits.', 'btn' => 'Apply now', 'link' => '#'],
    ['name' => 'Zoom', 'desc' => 'Empower your nonprofit with an exclusive 50% discount on Zoom\'s collaboration solutions.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'LinkedIn', 'desc' => '75% discount on LinkedIn\'s hiring and fundraising solutions.', 'btn' => 'Get started', 'link' => '#'],
    ['name' => 'Claude', 'desc' => 'Elevate your nonprofit’s writing and research with Claude AI at ~70% off.', 'btn' => 'Apply here', 'link' => '#'],
    ['name' => 'Microsoft', 'desc' => 'Power your nonprofit with free technology grants and discounts.', 'btn' => 'Get started', 'link' => '#'],
];
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Offers – EHEPS Organization</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body { background: #f8f9fa; }
        .sidebar-link { color: #6c757d; text-decoration: none; padding: 0.5rem 1rem; display: block; }
        .sidebar-link:hover, .sidebar-link.active { background: #e9ecef; border-radius: 0.375rem; color: #0d6efd; }
        .offer-card { transition: transform 0.2s; border: none; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .offer-card:hover { transform: translateY(-3px); box-shadow: 0 8px 16px rgba(0,0,0,0.1); }
        .banner-grants { background: #fff3cd; border: 1px solid #ffc107; border-radius: 0.5rem; padding: 1rem; }
        .footer { border-top: 1px solid #dee2e6; margin-top: 3rem; padding: 2rem 0; }
        .search-bar { max-width: 500px; }
    </style>
</head>
<body>
    <!-- Top Bar -->
    <div class="container py-2 d-flex justify-content-end align-items-center gap-3">
        <span class="text-muted small">EN</span>
        <a href="#" class="text-decoration-none text-primary">Get in touch</a>
    </div>

    <!-- Main Container -->
    <div class="container my-4">
        <div class="row">
            <!-- Sidebar -->
            <div class="col-lg-3 col-md-4 mb-4">
                <nav class="nav flex-column">
                    <a href="#" class="sidebar-link">Home</a>
                    <a href="#" class="sidebar-link">Profile</a>
                    <a href="#" class="sidebar-link">Donations</a>
                    <a href="#" class="sidebar-link">Payouts</a>
                    <a href="#" class="sidebar-link active">Product offers</a>
                    <a href="#" class="sidebar-link">My discounts</a>
                    <a href="#" class="sidebar-link">Grant Assistant</a>
                    <a href="#" class="sidebar-link">Goodstack Pro</a>
                </nav>
                <div class="banner-grants mt-4">
                    <strong>We have grants waiting for you!</strong>
                    <div class="mt-2"><a href="#" class="btn btn-warning btn-sm w-100">Apply now</a></div>
                </div>
            </div>

            <!-- Main Content -->
            <div class="col-lg-9 col-md-8">
                <!-- Header -->
                <div class="d-flex align-items-start gap-3 mb-4">
                    <div class="bg-light rounded-circle d-flex align-items-center justify-content-center" style="width: 80px; height: 80px; font-size: 2.5rem; color: #6c757d;">
                        <i class="bi bi-boxes"></i>
                    </div>
                    <div>
                        <h2 class="mb-1">Mohammad ewaz Nazari</h2>
                        <p class="text-muted mb-0">Owner</p>
                        <small class="text-muted"><?= $owner_email ?></small>
                    </div>
                </div>

                <!-- Search -->
                <h3 class="mb-3">Product offers</h3>
                <div class="mb-4">
                    <label class="form-label fw-bold">What are you looking for?</label>
                    <div class="input-group search-bar">
                        <input type="text" class="form-control" placeholder="Search for tools or key words">
                        <button class="btn btn-outline-secondary" type="button">Search</button>
                    </div>
                </div>

                <!-- Featured -->
                <h5 class="mt-4 mb-3">Featured deals</h5>
                <div class="row g-3 mb-4">
                    <?php foreach ($featured as $item): ?>
                    <div class="col-md-6 col-lg-4">
                        <div class="card offer-card h-100">
                            <div class="card-body d-flex flex-column">
                                <h6 class="card-title fw-bold"><?= htmlspecialchars($item['name']) ?></h6>
                                <p class="card-text small text-muted flex-grow-1"><?= htmlspecialchars($item['desc']) ?></p>
                                <a href="<?= htmlspecialchars($item['link']) ?>" class="btn btn-outline-primary btn-sm mt-2 align-self-start"><?= $item['btn'] ?></a>
                            </div>
                        </div>
                    </div>
                    <?php endforeach; ?>
                </div>

                <!-- Top Tools -->
                <h5 class="mt-4 mb-3">Top tools and resources</h5>
                <div class="row g-3 mb-4">
                    <?php foreach ($top_tools as $item): ?>
                    <div class="col-md-6 col-lg-4">
                        <div class="card offer-card h-100">
                            <div class="card-body d-flex flex-column">
                                <h6 class="card-title fw-bold"><?= htmlspecialchars($item['name']) ?></h6>
                                <p class="card-text small text-muted flex-grow-1"><?= htmlspecialchars($item['desc']) ?></p>
                                <a href="<?= htmlspecialchars($item['link']) ?>" class="btn btn-outline-primary btn-sm mt-2 align-self-start"><?= $item['btn'] ?></a>
                            </div>
                        </div>
                    </div>
                    <?php endforeach; ?>
                </div>

                <!-- Expert Services -->
                <h5 class="mt-4 mb-3">Expert services</h5>
                <div class="row g-3 mb-4">
                    <?php foreach ($expert_services as $item): ?>
                    <div class="col-md-6 col-lg-4">
                        <div class="card offer-card h-100">
                            <div class="card-body d-flex flex-column">
                                <h6 class="card-title fw-bold"><?= htmlspecialchars($item['name']) ?></h6>
                                <p class="card-text small text-muted flex-grow-1"><?= htmlspecialchars($item['desc']) ?></p>
                                <a href="<?= htmlspecialchars($item['link']) ?>" class="btn btn-outline-primary btn-sm mt-2 align-self-start"><?= $item['btn'] ?></a>
                            </div>
                        </div>
                    </div>
                    <?php endforeach; ?>
                </div>

                <!-- Discounted Software (including GitHub & MCP) -->
                <h5 class="mt-4 mb-3">Discounted software</h5>
                <div class="row g-3">
                    <?php foreach ($discounted_software as $item): ?>
                    <div class="col-md-6 col-lg-4">
                        <div class="card offer-card h-100">
                            <div class="card-body d-flex flex-column">
                                <h6 class="card-title fw-bold"><?= htmlspecialchars($item['name']) ?></h6>
                                <p class="card-text small text-muted flex-grow-1"><?= htmlspecialchars($item['desc']) ?></p>
                                <a href="<?= htmlspecialchars($item['link']) ?>" class="btn btn-outline-primary btn-sm mt-2 align-self-start"><?= $item['btn'] ?></a>
                            </div>
                        </div>
                    </div>
                    <?php endforeach; ?>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="footer">
        <div class="container text-center">
            <p class="mb-1"><strong>Domains:</strong> 
                <?php foreach ($domains as $d): ?>
                    <a href="https://<?= $d ?>" target="_blank"><?= $d ?></a> &nbsp;
                <?php endforeach; ?>
            </p>
            <p class="mb-0">
                <strong>Contact:</strong> 
                <?php foreach ($super_admins as $email => $role): ?>
                    <a href="mailto:<?= $email ?>"><?= $email ?></a> (<?= $role ?>) &nbsp;|&nbsp;
                <?php endforeach; ?>
                <a href="mailto:<?= $owner_email ?>"><?= $owner_email ?></a> (Owner)
            </p>
            <p class="mt-2 small text-muted">&copy; 2026 EHEPS Organization. All rights reserved.</p>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
