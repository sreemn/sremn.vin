<script lang="ts">
    import ConstructionIcon from "@lucide/svelte/icons/construction";
    import ExternalLinkIcon from "@lucide/svelte/icons/external-link";
    import * as Item from "$lib/components/shadcn-svelte/item/index.js";
    import Button from "$lib/components/shadcn-svelte/button/button.svelte";
    import { AspectRatio } from "$lib/components/shadcn-svelte/aspect-ratio/index.js";
    import RotiBotImage from "$lib/assets/roti_Banner.webp?url";
    import fredFMBotImage from "$lib/assets/fredFM_Banner.webp?url";

    import type { Project } from "$types";

    const projects: Project[] = [
        {
            name: "fredFM Bot",
            description:
                "Robust music app built for a private Discord community with seamless audio playback.",
            image: fredFMBotImage,
            button: {
                label: "Github",
                icon: ExternalLinkIcon,
                props: {
                    href: "https://github.com/sreemn/fredFM",
                    target: "_blank",
                },
            },
        },
        {
            name: "R.O.T.I Bot",
            description:
                "A versatile and powerful app to empower your server.",
            image: PortableMediaPlayerImage,
            button: {
                label: "Read more",
                icon: ConstructionIcon,
                props: {
                    disabled: true,
                },
            },
        },
    ];
</script>

<section class="my-16">
    <h2>Projects</h2>
    <p class="text-muted-foreground mt-1 text-sm">What I’ve been working on</p>

    <div class="my-4">
        <Item.Group
            class="grid grid-cols-1 xs:grid-cols-2 md:grid-cols-3 gap-4"
        >
            {#each projects as project (project.name)}
                <Item.Root
                    variant="outline"
                    class="rounded-2xl p-4 max-w-none flex-col justify-between items-stretch"
                >
                    <div class="space-y-3.5">
                        <Item.Header>
                            <AspectRatio
                                ratio={16 / 9}
                                class="bg-muted rounded-lg"
                            >
                                <img
                                    src={project.image}
                                    alt={project.name}
                                    draggable={false}
                                    class="h-full w-full rounded-lg object-cover"
                                />
                            </AspectRatio>
                        </Item.Header>
                        <Item.Content>
                            <Item.Title>{project.name}</Item.Title>
                            <Item.Description class="hyphens-auto"
                                >{project.description}</Item.Description
                            >
                        </Item.Content>
                    </div>
                    <Item.Footer class="*:w-full basis-auto">
                        <Button variant="outline" {...project.button.props}>
                            {#if project.button.icon}
                                {@const Icon = project.button.icon}
                                <Icon />
                            {/if}
                            {project.button.label}
                        </Button>
                    </Item.Footer>
                </Item.Root>
            {/each}
        </Item.Group>
    </div>
</section>
