# Windows virtual dedicated server hosting: what the monthly price really covers, VDS vs VPS vs bare metal, and how many RDP users before the bill jumps

Windows virtual dedicated server hosting gets quoted in three parts, and most price lists show you only the first one. The virtual machine is one line. The Windows Server licence is the second. The third is a per-person Remote Desktop licence once more than two admins need to be logged in at the same time. On a 4-vCPU box those last two lines add roughly $34 a month, which is enough to turn the cheaper-looking host into the more expensive one by the end of the year.

Below: what a virtual dedicated server actually is, how the licensing models differ, how many people you can put on one machine before the maths changes, which Windows version to install, and what SpinServers' current hardware list costs over twelve months.

> **Quick pick:** for a Windows workload that needs pinned resources and one or two admins, SpinServers' entry configuration at $79/month gives you 4 cores, 32 GB RAM and 1 TB NVMe on a single-tenant machine with Windows available as an auto-install. Licence cost sits on top, so confirm it in the quote. 👉 [See the current SpinServers configurations and monthly pricing](https://bit.ly/Spinservers)

## The full plan list, with the twelve-month cost

Four configurations are publicly listed, all month-to-month with no setup fee, all in Dallas or Silicon Valley.

| Configuration | CPU and RAM | Storage | Bandwidth and network | Price (and 12-month cost) | Order |
| --- | --- | --- | --- | --- | --- |
| Intel Xeon E3-1280 v5 | 4 cores, 32 GB RAM | 1 TB NVMe SSD | 30 TB, 2 × 10 Gbps ports | $79/mo ($948/yr) | [Check this configuration](https://bit.ly/Spinservers) |
| Starter Package | Cores not listed, 32 GB RAM | 1 TB NVMe SSD | 10 TB, 10 Gbps | $99/mo ($1,188/yr) | [Check the Starter Package](https://bit.ly/Spinservers) |
| Growth Package | 256 GB RAM | 2 × 1.6 TB SSD | 20 TB, 10 Gbps | $149/mo ($1,788/yr) | [Check the Growth Package](https://bit.ly/Spinservers) |
| High Performance Package | 768 GB RAM | 8 × 2 TB SSD | 40 TB, 10 Gbps | $679/mo ($8,148/yr) | [Check the High Performance Package](https://bit.ly/Spinservers) |

Two things in that table are worth pausing on. The $79 entry listing carries a larger bandwidth allowance (30 TB) than the $99 listing (10 TB), which reads like two different stock batches rather than a deliberate tier ladder, so verify the allowance on the order page. And the Starter Package listing does not state a core count, only RAM. If core count decides your purchase, ask before you pay rather than after.

Everything is single-tenant hardware. There is no hypervisor slicing your box in half, which is the property that puts these machines at the top of the "dedicated resources" spectrum rather than in the middle.

## What the infrastructure includes, and what isn't published

Each server ships with one IPv4 address and an IPv6 /64 block, sits on a DDoS-protected multihomed network, and comes with IPMI or iKVM remote management, so you can reach the console even after a firewall rule locks you out of RDP. Provisioning is automated, with Linux, Windows and ESXi as install options. Support runs 24/7 over email, phone, tickets and live chat. The facilities are advertised as SOC 2, HIPAA and PCI compliant, with the caveat that the PCI work is your own; managed compliance and scanning are not part of the offer. Third-party reviews cite a 99.999% uptime SLA, though the compensation terms behind that figure are not published, so treat it as a marketing number rather than a contract you can price.

Three things are not published and matter at checkout: the per-plan price of a Windows Server licence, the refund terms (month-to-month service is generally sold without a refund window, so size the machine before you buy, not after), and pricing for any virtual or cloud tier, since the public list covers dedicated hardware. If you specifically need a VM with pinned vCPUs rather than a whole chassis, ask their sales team what the current virtual line looks like.

## Windows licensing is where two quotes stop being comparable

Hosts handle the Microsoft licence in one of two ways, and the gap between them is the single biggest source of bad price comparisons.

**Bundled.** Some providers fold the Windows Server licence into the plan price. Apps4Rent, for example, starts virtual dedicated servers at $26.95/month with the Windows Server licence included, and bills RDS client access licences, Microsoft 365, SQL Server above Express and application licences separately. The headline number is close to your real number, with those named exceptions.

**Evaluation plus per-core.** Others ship Windows as an evaluation install with no upfront licence cost, then charge per vCPU. MassiveGRID prices the licence at $6.31 per vCPU, or you run the 180-day evaluation. The mechanics of that evaluation are the part nobody reads: the template must be activated online within the first 10 days, runs fully for 180 days with a countdown on the desktop, and after day 180 the server keeps your data and software but shuts down once an hour and accepts only security updates until a licence is added. Adding the licence is an in-place conversion, so no reinstall.

Take a 4-vCPU machine: the licence line is $25.24 a month under the per-core model, or $0 for the first six months and then mandatory if you want to keep working. A $26.95 bundled quote and a $18.84 host-plus-licence quote can therefore land in the same place, or $300 a year apart, depending on which model each one uses.

Desktop Windows follows a different rule. Microsoft does not let hosting providers rent out Windows 10 or 11 licences, so those templates install unactivated and you supply your own product key after first login. If a quote offers you Windows 11 Pro "included", ask what key you are being given.

> Before you compare two Windows hosts, get one sentence in writing from each: is the Windows Server licence inside this monthly price, and what happens on day 181? 👉 [Ask SpinServers the same question while you check their plan pricing](https://bit.ly/Spinservers)

## How many people will be logged in at once?

Two administrative RDP sessions are included by default on a Windows server. The third concurrent user is where money starts moving: extra RDP user licences run $8.90 per user per month at MassiveGRID, and RDS client access licences are billed separately at Apps4Rent. Under a full Remote Desktop Services deployment, CALs are a separate purchase again.

Put numbers on a three-person team on a 4-vCPU machine priced the per-core way:

- Host: the plan price
- Windows Server licence: 4 × $6.31 = $25.24/month
- Third concurrent user: 1 × $8.90 = $8.90/month
- Added cost over the host fee: $34.14/month, or $409.68/year

That $409 is the number that never appears in a comparison table. It is also why "how many people will actually log in" belongs in the first paragraph of your requirements, not the last. If the answer is "three or more, all day", you are past the point where a shared-vCPU VPS makes sense, and you want reserved cores: MassiveGRID draws that line at its $18.84/month dedicated VPS tier, and on a SpinServers machine the cores are yours by definition because nobody else is on the box.

RDP itself is not the constraint people fear. Sessions survive a closed window, so scheduled jobs, trading terminals and bots keep running after you disconnect, and clients exist for Windows, macOS, iOS, Android and Linux.

## VDS, VPS and bare metal: where the premium actually goes

A virtual dedicated server is a virtual machine running on physical hardware through a hypervisor such as Microsoft Hyper-V. Type-1 hypervisors sit directly on the hardware and carve the machine into isolated VMs, each with its own RAM, vCPU and storage allocation. You get administrator rights and a fixed resource envelope without paying for an entire chassis.

The distinction from a standard VPS is not "virtual versus real". Both are virtual. It is whether your resources can be sold twice.

|  | Virtual dedicated server | VPS | Bare metal |
| --- | --- | --- | --- |
| Resource allocation | Guaranteed, fixed, not shared | Can be oversold across tenants | Whole machine, one customer |
| Typical starting price | From $26.95/month | Often under $10/month | Typically $100+/month |
| Admin access | Full administrator | Full root on most plans | Full root plus hardware access |
| Performance consistency | Consistent, hypervisor-isolated | Variable, depends on neighbours | Highest, no virtualisation layer |
| Setup time | Hours | Near-instant | Days to weeks |
| Fits | SMBs, developers, resellers needing guaranteed resources | Entry projects, low-traffic sites | High-performance, compliance-heavy workloads |

The setup-time row catches people out. A VDS is typically provisioned within hours, not seconds, and bare metal has historically meant days to weeks of build time. SpinServers' automated provisioning is the reason its dedicated list belongs in the same conversation as a VDS on turnaround, even though the hardware tier is higher.

Who should not pay the premium: a single low-traffic IIS site, a test box, a one-person remote desktop for an accounting package. A $4 to $10 VPS handles those, and the guarantee buys you nothing you will notice. The premium earns its keep when a noisy neighbour would show up in your invoices, meaning databases, multi-user line-of-business software, or anything where a 20% CPU steal turns into a missed deadline.

## Which Windows version to install

Windows Server 2025 is the default for new servers, and 2016, 2019 and 2022 stay available for software that has not been certified on the newer releases. Most workloads that need Windows at all want Windows Server, because it gives you two RDP sessions out of the box, runs IIS, SQL Server and the Windows business applications you already own, and is the edition a hosting provider can license on your behalf.

Windows 11 Pro is the right pick in two situations only: the application has been tested on desktop Windows and nowhere else, or you already own a key you want to reuse. Desktop editions allow a single interactive session, so they cannot serve a three-person team. Windows 11 Pro also needs at least 2 GB of RAM, which is why configurators start it at 2 GB where a Windows Server install can run on 1 GB.

Windows 10 left support on 14 October 2025 and no longer receives security updates. New deployments belong on Windows 11 Pro or Windows Server.

One caveat on older releases: some hosts still list Windows Server 2008 R2 and 2012 R2 as installable options without stating their support status. Being installable and being patched are different things. If a legacy application forces you onto an old release, plan on isolating that machine from the public internet rather than assuming the host has you covered.

## The first hour on a freshly provisioned Windows server

RDP in with the IP and credentials you were sent, then work through this before you install anything:

1. Run Windows Update and reboot until it comes back clean.
2. Restrict RDP to trusted source IPs or a VPN, and move it off the default port. Add network-level authentication and, if your access method supports it, a second factor.
3. Set strong, unique passwords for every component you install, and rename or disable the default administrator account.
4. Remove roles and services you are not using. Every one you leave running is an entry point.
5. Install what the workload needs: IIS, .NET, SQL Server, then DNS if you are hosting sites.
6. Configure backups and basic monitoring, and test a restore before you trust either.

Keep the IPMI or KVM console details somewhere you can reach without the server. A firewall rule that blocks your own RDP access is the most common way people lock themselves out of a machine they are paying for, and console access is the only way back in.

Assume self-management unless a plan says otherwise. The Windows VPS tiers at MassiveGRID and Contabo are both unmanaged, with support covering the infrastructure layer only; patching, backups and monitoring are yours. Fully managed Windows with OS patching and monitoring sits on a separate, more expensive product line.

## Costs and limits that show up after month one

**The licence question, again.** SQL Server Express is free; Web and Standard editions need a licence you supply, or a plan that explicitly bundles SQL Server Web. A "Windows VPS" that runs your database fine in month one can turn into a licensing project in month three.

**Backups and IPs are line items.** At Apps4Rent, offsite backup runs $20 to $45 per month depending on plan, and each additional public IP is $3.50 per month. On a $26.95 plan, backup alone can add 75% to the bill.

**Operating system changes usually mean a new order.** IONOS states plainly that a Windows virtual server cannot be switched to another operating system later; moving to Linux requires placing a new order. Decide the OS before you provision, or pick a product line that allows rebuilding.

**Cheap tiers are shared vCPU.** The $3.99/month Windows VPS tier at MassiveGRID is shared vCPU; only the Windows Dedicated VPS tier at $18.84/month reserves cores and RAM. Databases, IIS under load, three or more RDP users and emulator farms all belong on the reserved tier.

**Month-to-month cuts both ways.** No long contract means you can leave, and it also usually means no refund window. Test on the smallest configuration that could plausibly work, then scale up.

## Picking a configuration

Match the machine to the workload rather than to the price you hoped for:

- **One admin, one application, a light IIS site or a bot:** the $79 configuration is already more machine than the job needs, and it is the cheapest way onto single-tenant Windows hardware here.
- **Three or more concurrent RDP users, SQL Server Standard, or IIS under load:** reserved cores are non-negotiable. Start at the 32 GB configurations and treat RAM as the first thing you upgrade, since every RDP user adds a session's worth of memory pressure.
- **Large local databases, VMs inside the box, emulator or automation farms:** the Growth Package at $149/month with 256 GB RAM, or the High Performance Package at $679/month with 768 GB and eight 2 TB SSDs, is where those workloads stop fighting the hardware.

Two questions to settle before you enter card details. First, is the Windows Server licence included in the monthly figure, or are you bringing your own or starting a 180-day clock? Second, does the quoted monthly rate hold on renewal, and what are the refund terms if the machine turns out to be the wrong size? Neither answer is on the public plan list, and both change the twelve-month cost more than the difference between two adjacent tiers.

👉 [Start with the $79 configuration at SpinServers and confirm the licence terms with their team](https://bit.ly/Spinservers)
