<script>
    import Logo from "../Icon.svelte";
    import { onMount } from "svelte";

    let workspaceList = [];
    onMount(() => {
        workspaceList = [];
    });

    function addWorkspace() {
        let randomString;
        const characters = "abcdefghijklmnopqrstuvwxyz0123456789";
        const length = 6;
        let result = "";

        for (let i = 0; i < length; i++) {
            const randomIndex = Math.floor(Math.random() * characters.length);
            result += characters.charAt(randomIndex);
        }

        randomString = result;

        workspaceList = [
            ...workspaceList,
            { id: randomString, name: "새로운 워크스페이스" },
        ];
        console.log(workspaceList);
    }

    function editWorkspaceName(name) {
        workspaceList = workspaceList.map((workspace) => {
            if (workspace.id === id) {
            }
        });
    }
</script>

<button
    data-drawer-target="default-sidebar"
    data-drawer-toggle="default-sidebar"
    aria-controls="default-sidebar"
    type="button"
    class="inline-flex items-center p-2 mt-2 ml-3 text-sm text-gray-500 rounded-lg sm:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
>
    <span class="sr-only">Open sidebar</span>
    <svg
        class="w-6 h-6"
        aria-hidden="true"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
    >
        <path
            clip-rule="evenodd"
            fill-rule="evenodd"
            d="M2 4.75A.75.75 0 012.75 4h14.5a.75.75 0 010 1.5H2.75A.75.75 0 012 4.75zm0 10.5a.75.75 0 01.75-.75h7.5a.75.75 0 010 1.5h-7.5a.75.75 0 01-.75-.75zM2 10a.75.75 0 01.75-.75h14.5a.75.75 0 010 1.5H2.75A.75.75 0 012 10z"
        />
    </svg>
</button>
<aside
    id="default-sidebar"
    class="fixed top-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full sm:translate-x-0"
    aria-label="Sidenav"
>
    <div
        class="overflow-y-auto py-5 px-3 h-full bg-white border-r border-gray-200 dark:bg-gray-800 dark:border-gray-700"
    >
        <a href="/" class="flex items-center justify-center w-full pb-5">
            <Logo />
        </a>
        <hr />
        <ul class="space-y-2 mt-5">
            <li class="mb-4">
                <div
                    class="flex items-center justify-between px-2 text-gray-700"
                >
                    <p class="text-sm">워크스페이스</p>
                    <button
                        on:click={addWorkspace}
                        type="button"
                        class="rounded-full hover:bg-gray-100 bg-white w-6 h-6 flex items-center justify-center"
                    >
                        <i class="fa-solid fa-plus text-sm" />
                    </button>
                </div>
            </li>
            {#each workspaceList as list}
                <li>
                    <button
                        on:dblclick={() => editWorkspaceName}
                        class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group w-full"
                    >
                        <i class="fa-solid fa-file ml-1" />
                        <span class="ml-2">{list.name}</span>
                    </button>
                </li>
            {/each}
        </ul>
    </div>
    <div
        class=" absolute bottom-0 left-0 justify-center p-4 space-x-4 w-full lg:flex bg-white dark:bg-gray-800 z-20 border-r border-gray-200 dark:border-gray-700"
    />
</aside>
