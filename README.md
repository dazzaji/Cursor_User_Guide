# Dazza Greenwood's Guide to Cursor

This are my full Cursor user guide and notes.  
Last Revised: February 22, 2025

## Introduction to Cursor AI

Cursor AI is an AI-powered code editor designed to streamline software development by integrating advanced language models directly into your coding workflow. Built on a foundation similar to Visual Studio Code, it provides a familiar interface while adding powerful AI features for code completion, intelligent suggestions, and context-aware assistance ([Cursor AI: A Guide With 10 Practical Examples | DataCamp](https://www.datacamp.com/tutorial/cursor-ai-code-editor#:~:text=Cursor%20AI%20is%20an%20AI,with%20the%20platform%20to%20transition)) ([Cursor for Developers: Ultimate Introduction](https://www.builder.io/blog/cursor-ai-for-developers#:~:text=Cursor%20is%20basically%20an%20AI,capabilities%20to%20a%20familiar%20interface)). With Cursor, you can write and modify code using natural language prompts, get explanations for code segments, and even have the AI perform multi-step coding tasks.

**Key Features:**

- **AI Code Autocomplete:** Cursor offers multi-line code completions and smart predictions as you type. It analyzes your context and recent changes to suggest the next lines of code or entire blocks, not just trivial single-line hints ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Tab)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Cursor%20includes%20a%20powerful%20autocomplete,into%20account%20your%20recent%20changes)). This helps you write code faster and catch mistakes early.
- **Chat Assistant (AI Sidebar):** A built-in chat interface lets you talk to an AI that is aware of your code. You can ask questions about your codebase, get bug fixes or optimization suggestions, and even apply changes from chat with one click ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Chat)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Instant%20Apply)).
- **Composer & Agent:** An advanced prompt tool (Composer) allows you to describe high-level changes or new features, and Cursor will implement them. In *Agent* mode, the AI can take autonomous actions (like editing multiple files or running build/test commands) to accomplish a goal, while you supervise the process ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=AI%20assistant%20that%20uses%20tools,coding%20tasks%20with%20minimal%20supervision)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Agent)).
- **Documentation & Web Integration:** Cursor can incorporate external resources. Use `@Docs` to add and reference official library documentation within the editor, or `@Web` to fetch up-to-date information from the internet without leaving your IDE ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Ask%20the%20Web)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Get%20up,information%20to%20answer%20your%20question)).
- **Codebase Understanding:** Cursor indexes your project’s code to provide context-aware answers. It can refer to your entire codebase when answering questions (using `@codebase`) and adhere to project-specific patterns or rules you define ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Codebase%20Answers)) ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Using%20rules%20in%20Cursor%20you,a%20system%20prompt%20for%20LLMs)).
- **Custom AI Rules:** You can define rules that guide the AI’s style and behavior (for example, coding style guidelines or preferences for certain frameworks). These rules help ensure AI-generated code follows your project’s requirements ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Using%20rules%20in%20Cursor%20you,a%20system%20prompt%20for%20LLMs)) ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Project%20Rules%20)).
- **Security Controls:** Cursor is designed with security in mind – it offers features like Privacy Mode to avoid storing your code on servers, and it respects ignore files to exclude sensitive or irrelevant parts of your codebase from AI processing ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=We%20depend%20on%20the%20following,see%20%209%20section)) ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Cursor%20uses%20the%20same%20package,committing%20it%20to%20the%20repository)).

In the rest of this guide, we’ll cover how to install and set up Cursor, explain its core components, explore advanced capabilities, and provide tips for getting the most out of this AI-assisted development tool.

## Installation and Setup

**Downloading Cursor:** Cursor is available for Windows, macOS, and Linux. Visit the [official Cursor website](https://cursor.com) and click the **Download** button ([Cursor – Installation](https://docs.cursor.com/get-started/installation#:~:text=Installation)). Run the installer for your platform and follow the prompts to install Cursor. On Linux, the download is an AppImage – make it executable (`chmod +x cursor-<version>.AppImage`) and run it to launch the application ([Cursor AI: A Guide With 10 Practical Examples | DataCamp](https://www.datacamp.com/tutorial/cursor-ai-code-editor#:~:text=In%20Linux%2C%20it%20comes%20as,to%20make%20it%20executable%20using)).

**Initial Configuration:** On first launch, Cursor will guide you through a few setup steps ([Cursor – Installation](https://docs.cursor.com/get-started/installation#:~:text=Setting%20up)):

- *Keyboard Shortcuts:* Choose the keybinding presets. By default, Cursor uses VS Code’s shortcuts, but you can opt for others (Vim, Sublime, etc.) if you prefer ([Cursor – Installation](https://docs.cursor.com/get-started/installation#:~:text=%2A%20Keyboard%20shortcuts%20,commands%20to)). Selecting the VS Code keymap is recommended for most, as it will feel familiar.
- *Interface Language:* Select the language for AI responses. English is default, but you can set another language if you want the AI to reply in, say, Spanish or Chinese ([Cursor – Installation](https://docs.cursor.com/get-started/installation#:~:text=%2A%20Keyboard%20shortcuts%20,commands%20to)). (This can also be changed later in the settings or via rules.)
- *Codebase Indexing:* Decide whether to enable codebase indexing. Indexing allows Cursor to preprocess your project for better context (more on this in **Working with Projects**). It’s usually beneficial to enable this so the AI can “see” your whole project for context ([Cursor – Installation](https://docs.cursor.com/get-started/installation#:~:text=can%20enter%20the%20name%20of,launch%20Cursor%20from%20the%20terminal)).
- *CLI Shortcuts:* Optionally, install the `cursor` command-line launcher. This lets you open Cursor from a terminal (similar to how `code` launches VS Code) ([Cursor – Installation](https://docs.cursor.com/get-started/installation#:~:text=%2A%20Codebase%20Indexing%20,launch%20Cursor%20from%20the%20terminal)).

After this quick configuration, Cursor will start and you’ll be ready to use its AI features. If you’re coming from VS Code, you can even import some settings or have Cursor open your previous projects (it’s compatible with VS Code workspaces and settings to a large extent).

**Signing In:** You can use Cursor without an account in free mode. However, signing in (with GitHub or email) might be required to access pro features or higher-tier models (like GPT-4 or Claude-v3.5) depending on the plan. Check **Cursor Settings > Account** if you need to upgrade or sign in for additional features.

## Core Features and Interface

Once installed, Cursor’s interface will look familiar if you’ve used VS Code. You have a file explorer on the side, a text editor pane, and a bottom panel for terminal or output. The key addition is the AI sidebar and composer panel, plus some new commands and shortcuts for interacting with the AI.

### Autocompletion and Tab Predictions

Cursor’s AI autocomplete (the **Tab** feature) is always at work as you code. It uses the context in the current file and your recent edits to predict what you might write next ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Cursor%20includes%20a%20powerful%20autocomplete,into%20account%20your%20recent%20changes)). Simply start typing, and you may see a grayed-out suggestion for the next part of your code. Press **Tab** to accept the suggestion. Unlike basic editors, Cursor’s suggestions can span multiple lines and even update based on changes you just made (for example, if you declare a new variable, it might adapt subsequent suggestions to use it) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Tab)).

Key points about autocomplete:

- **Multi-line Suggestions:** Cursor can complete whole lines or blocks at once. For example, if you type the beginning of a function or a loop, it might suggest the entire structure including curly braces and some placeholder logic ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Cursor%20includes%20a%20powerful%20autocomplete,into%20account%20your%20recent%20changes)). This reduces repetitive typing.
- **Smart Continuation:** The AI looks at the function or class you’re in to continue logically. If you’re in the middle of an object initialization, it might suggest the remaining fields. If you write a comment saying `// TODO: validate input`, it might even generate code to do that.
- **Partial Acceptance:** If a suggestion is mostly correct but slightly too long, you can accept part of it. By pressing <kbd>Ctrl</kbd>+<kbd>Right Arrow</kbd> (or <kbd>Cmd</kbd>+<kbd>Right</kbd> on Mac), you accept the next word of the suggestion, allowing you to step through a long suggestion word-by-word ([Cursor – Advanced Features](https://docs.cursor.com/tab/advanced-features#:~:text=You%20can%20accept%20the%20next,to%20your%20preferred%20keybinding)). This gives fine-grained control to ensure the code is exactly what you want.
- **Continuous Learning:** The suggestions adapt as you edit. If you reject a suggestion and type something else, Cursor learns from that context. It will use your file’s content and coding style to improve future suggestions (though it doesn’t learn across different projects unless you encode that in rules).

Autocomplete is meant to assist rather than dominate your coding – you remain in charge. Always review AI-generated code, especially for critical logic. You can disable inline suggestions or adjust their behavior in **Settings** if needed (for instance, you can require an explicit shortcut to trigger suggestions if you find them too distracting when always-on).

### Chat Sidebar: AI Assistant

One of Cursor’s most powerful features is the **Chat** sidebar, which functions as an AI pair programmer. To open the chat panel, click the “AI” icon or press **Cmd+L** (Mac) / **Ctrl+L** (Windows/Linux) ([All Cursor Shortcuts Guide: Composer, AI Pane, and more. - Refined](https://refined.so/blog/cursor-shortcuts-guide#:~:text=Refined%20refined,MacOS%29%20or%20CTRL)). This opens a conversation interface where you can ask the AI questions or give instructions in natural language.

**What the Chat Knows:** The chat AI is aware of your current coding context. It automatically has access to the content of the file you’re currently working on and even the specific code around your cursor selection ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Chat)). For example, if your cursor is on a function, you can ask *“What does this function do?”* and the AI will analyze that function’s code to answer. You don’t always need to copy-paste code into the chat; the AI sidebar sees what you see in the editor.

**Using Chat for Assistance:** You can ask the AI to explain code, suggest improvements, find bugs, or even write new code. Some examples:

- *“Explain the purpose of the `ProcessData()` function.”* – The AI will read that function and describe what it does in plain language.
- *“I’m getting an IndexError on line 45. What might be the cause?”* – The AI will consider line 45 in context and suggest possible reasons (e.g. list out of range) and fixes.
- *“Write a unit test for the `LoginService` class.”* – The AI can generate a test function or suite, referencing the code in `LoginService` to cover its behavior.

When the AI provides a code solution or example in its answer, you can often **apply** it directly to your code. Cursor’s chat shows an “apply change” button (a play icon) on AI-generated code blocks; clicking it will insert or replace the code in your editor with that suggestion ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Instant%20Apply)). This one-click apply makes it easy to implement the AI’s fixes or improvements, but always review the diff (Cursor will usually show you the changes before they go live).

**Context and Referencing:** By default, the chat includes the current file as context. You can expand the context by bringing in other files or data – see **Context Injection with @ Symbols** below for how to do that. For instance, you could ask *“How does `ModuleA` interact with `ModuleB`?”* and include both files in the question using @ references. The richer the context you provide, the more accurate the answers will be.

**Model Selection:** At the top of the chat panel, there’s a dropdown to choose the AI model for the conversation. Cursor supports multiple models (like GPT-4, GPT-3.5, Claude, etc.). By default it picks a capable model available to your plan. You might use a faster model (GPT-3.5) for quick Q&A, and switch to a more advanced one (GPT-4 or Claude 100k) for complex tasks or when dealing with very large files. You can switch models mid-conversation if needed, but note that the conversation history may not carry over to the new model, so it’s usually best to start a fresh chat when changing models significantly.

**Keeping History:** The chat remembers the conversation (up to the model’s context limit). You can refer back to things you discussed earlier in the same chat session. However, long chats can consume a lot of context window; if the discussion becomes too long-winded or goes off track, it’s often effective to start a new chat session focused on the specific issue.

**Tip:** Use chat for exploratory questions, debugging, or getting quick advice. For very specific code generation tasks that involve multiple files or a sequence of steps, the Composer (next section) might be more efficient. But the line between Chat and Composer is flexible – use whichever feels appropriate. Many users treat the chat as a sounding board or a junior developer: you ask it for insight or drafts, then you refine and decide what to implement.

### Context Injection with @ Symbols

To get the best results from Cursor’s AI, especially in chat or composer prompts, you can inject additional context using the **`@` symbol** system. Cursor allows you to refer to files, folders, or other resources by typing `@` in any prompt, which brings up a menu of options ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=In%20Cursors%20input%20boxes%2C%20such,suggestions%20based%20on%20your%20input)) ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=Here%E2%80%99s%20the%20list%20of%20all,symbols%20available)).

Here are the most commonly used `@` references:

- **`@Files`:** Typing `@` followed by a filename (or selecting **Files** in the menu) will attach the contents of that file to your question ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=Here%E2%80%99s%20the%20list%20of%20all,symbols%20available)). For example, in chat you might write: *“@UserController.ts What are some improvements we can make to this file?”* – the AI will read the `UserController.ts` file and then give suggestions.
- **`@Folders`:** You can similarly add all files in a folder by referencing the folder name ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=%2A%20%40Files%20,files%20in%20your%20project)). For instance, *“@utils/ summarize what this folder is for.”* (Be cautious: adding a large folder means a lot of content; ensure the model can handle it or consider summarizing the folder first.)
- **`@Code` (Symbols):** This lets you reference a specific code symbol (like a function, class, or variable) by name ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=%2A%20%40Files%20,files%20in%20your%20project)). If you have an indexed codebase, you could do something like: *“@Code DatabaseConnection how is this used across the project?”* and Cursor will find the symbol definition and usage.
- **`@Codebase`:** This special token includes an *overview* of your entire codebase context ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Codebase%20Answers)). It’s useful for broad questions. For example: *“@Codebase Are there any functions that are defined but never used?”* – Cursor will search the index for answers. (In the chat UI, pressing **Ctrl+Enter** after your question is a shortcut to include the whole codebase, equivalent to @Codebase ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Chat%20lets%20you%20talk%20with,with%20your%20entire%20codebase%20with%C2%A0Ctrl%2BEnter)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Use%20%40Codebase%20or%C2%A0Ctrl%C2%A0Enter%20to%20ask,relevant%20code%20to%20your%20query)).)
- **`@Docs`:** This is for documentation. If you have added external docs (see **Documentation Integration** in Advanced Features), you can bring them in by name. E.g., if you added React’s docs, you could type *“@Docs React useState example”* to fetch a relevant excerpt. The Cursor menu might list known libraries too (for popular frameworks Cursor might have some docs indexed already) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Use%20Documentation)).
- **`@Web`:** Use this to do a web search on the fly. Typing `@Web` in a prompt allows Cursor to fetch information from the internet for you ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Ask%20the%20Web)). For example: *“@Web latest changes in Python 3.12 asyncio”* would retrieve data from a web search which the AI can then summarize or incorporate.
- **Other @ references:** Cursor also provides `@Git` (to reference git commit history or diffs), `@Notepads` (perhaps for internal notes), and `@Cursor Rules` (to reference your rule files), among others ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=%2A%20%40Code%20,or%20symbols%20from%20your%20codebase)) ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=%2A%20%40Summarized%20Composers%20,with%20summarized%20composer%20sessions)). These are more specialized; for instance, `@Git` could be used to ask about what changed in a certain commit by referencing its ID.

When you invoke `@`, a drop-down will show categories and suggestions as you type, making it easy to find the file or resource you need. You can navigate this list with arrow keys and press Enter to select ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=Keyboard%20Shortcuts)). This inserts the reference into your prompt.

Using `@` symbols effectively means you don’t have to manually copy-paste code or text – it pulls the content in behind the scenes for the AI to use. This **context injection** is powerful: it lets the model access exactly the information you want it to consider. For example, to compare two files, you might do: *“Compare @Files src/OldAlgorithm.py with @Files src/NewAlgorithm.py and highlight differences.”* The AI will read both and give you an analysis.

Remember that the model has a context size limit (which varies by model). Don’t try to stuff too many huge files at once; if you need to, consider summarizing parts first or using a larger-context model like Claude. The `@` references are there to give precise control over context, so use them judiciously for the best results ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Reference%20your%20Code)).

### Inline Prompting with the Command Palette (⌘K / Ctrl+K)

Aside from the chat sidebar, Cursor provides a quick inline prompting feature via the **Command Palette** (similar to VS Code’s). Press **Cmd+K** (Mac) or **Ctrl+K** (Win/Linux) to bring up a small prompt bar at the top of the editor ([Are You Really Using the Prompt Bar (Cmd K) Feature Effectively?](https://cursor101.com/tutorial/learn-cursor-cmdk#:~:text=Are%20You%20Really%20Using%20the,to%20quickly%20get%20AI)) ([Cursor AI: A Guide With 10 Practical Examples | DataCamp](https://www.datacamp.com/tutorial/cursor-ai-code-editor#:~:text=trigger%20AI%20actions%20using%20keyboard,code%20based%20on%20your%20prompts)). This is sometimes called the *Prompt Bar* or *Inline Composer*. It allows you to send a one-off instruction to the AI about the code in the current file or selection.

Use cases for the prompt bar include: 

- **Refactoring a Selection:** Highlight a block of code, press Cmd+K, and type *“Refactor this to use async/await”* or *“Simplify this logic”*. The AI will return a suggestion, which you can accept to replace the highlighted code.
- **Generating Code Snippets:** Without leaving your editor or opening the chat, you can quickly ask for code. For example, place your cursor where you want new code and press Cmd+K, then type *“Generate a function that parses a URL string into a struct”*. The generated code will appear inline for you to review and accept.
- **Look up Definitions:** You can also use the `@Definitions` symbol via Cmd+K to jump to symbol definitions quickly ([Overview - Cursor](https://docs.cursor.com/context/@-symbols/overview#:~:text=%40Definitions%20,to%20the%20context%20without)) ([Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview#:~:text=%2A%20%40Codebase%20%20,43%20only)). This isn’t generating code, but it’s a handy navigation aid integrated into the palette.

The inline prompting is essentially a mini version of the Composer focused on the current file. It’s usually faster than opening a full chat, and it’s modal – meaning it pops up, you get a result, and then it closes. This is great for quick fixes or code generation tasks scoped to one place.

After the AI produces an inline suggestion, you’ll see a diff or preview of what it wants to do. Accepting the change will apply it to your file. If you don’t like it, you can reject it and keep your original code. Nothing is applied until you confirm.

**Note:** The inline prompt (Cmd+K) is context-aware: it knows about the current file and any selected text. It will **not** automatically consider your entire project unless you explicitly bring in more context (with @ symbols). So use it for localized tasks. For broader queries, the chat or composer might be more appropriate.

### The Composer (Normal vs Agent Modes)

The **Composer** is Cursor’s dedicated tool for handling larger or more complex prompts than the quick inline bar. While the chat sidebar is great for Q&A and incremental help, the Composer is ideal when you have a specific outcome in mind – e.g., “implement a new feature” or “perform these multiple changes” – and you want the AI to handle it in one go or with a controlled sequence of steps.

To open the Composer, use **Cmd+I** (Mac) / **Ctrl+I** (Win) or select it from the Cursor menu ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=Composer%20is%20your%20AI%20coding,to%20create%20a%20new%20Composer)). This opens a panel (often at the bottom or side) where you can write a prompt and execute it. You can also create a *new* Composer tab with **Cmd+N** within the Composer panel if you want to keep multiple prompt sessions separate ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=Composer%20is%20your%20AI%20coding,to%20create%20a%20new%20Composer)).

**Modes of Operation:** The Composer can run in two modes – **Normal** and **Agent** ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=Modes)). You can switch between these modes in the Composer UI (for example, via a toggle or dropdown that says “Mode: Normal | Agent”) before running your prompt ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Agent)).

#### Normal Mode

In Normal mode, the Composer acts like a sophisticated one-time prompt executor. You provide an instruction or description, and the AI will attempt to fulfill it by making direct changes to your code or generating new code, *all in one step*. This mode is generally faster and uses the AI in a straightforward way (no complex reasoning loops). All AI models supported by Cursor can operate in Normal mode ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=Normal)).

**How to use Normal mode:**

1. **Write a Prompt:** Describe what you want to do. Be as clear as necessary. For example: *“Create a new Python file `config.py` that defines a class Config with attributes url, timeout, and debug (with default values). Also update `main.py` to instantiate Config and print the config values.”* This prompt spans multiple tasks (new file + edit another).
2. **Execute:** Hit the run button (▶️) in the Composer. The AI will process the prompt. It has access to your open workspace and can read/write files directly (within the scope of this prompt).
3. **Review Changes:** Cursor will present you with the changes it intends to make. This usually comes as a **visual diff** for each file it wants to modify or create. For example, you might see a diff showing a new `config.py` file with content, and a diff of `main.py` with some lines added. Review these diffs carefully ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=When%20Composer%20suggests%20changes%3A)).
4. **Apply or Reject:** If everything looks good, click the **Accept** (✔️) button to apply all changes. If something is wrong, you can reject (✖️) to cancel. You can also partially accept by manually editing the diff before applying – the diff view is editable, so you could remove or tweak some changes and then accept.
5. **Iterate if needed:** After applying, you can run another prompt if further adjustments are needed. Each run in Composer is like a single transaction; Normal mode won’t automatically loop or refine without you prompting again.

Normal mode is great for contained tasks. For instance, “Add a new field to a struct and update all references” can be done in one shot – the AI will find all references and modify them. You save time because the AI does the mechanical parts. However, if the task requires some decision-making or debugging (something not achieved in the first try), you either run another composer prompt or switch to chat to figure out issues.

Under the hood, Normal mode is similar to how you might use ChatGPT with a system prompt that includes your entire project context plus the user prompt. It doesn’t do multiple rounds of reasoning; it’s a single round-trip. That’s why it’s usually quick and works with any model (even ones that can’t do long reasoning chains).

#### Agent Mode

Agent mode is a more experimental and powerful mode where the AI can perform **multi-step reasoning and execution** to accomplish a goal ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=AI%20assistant%20that%20uses%20tools,coding%20tasks%20with%20minimal%20supervision)). In this mode, the AI behaves like an “agent” that can use tools: it can read files, write to files, search your codebase, and even run shell commands as needed to complete the task you give it ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=Tools)). It will plan a series of steps and attempt them one by one, adjusting as necessary.

When you switch the Composer to Agent mode (select “Agent” in the mode selector) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Agent)), you use it as follows:

1. **Describe the Task:** Provide a high-level instruction, possibly something that requires multiple actions. For example: *“Migrate the project’s database from SQLite to PostgreSQL. Update all configuration files for Postgres, refactor any raw SQL queries if needed, then run the test suite to ensure everything passes.”* This is a complex task involving config changes and running tests.
2. **Run the Agent:** Click run. The Agent will start by breaking down your instruction into sub-tasks. You will see in the Composer panel a step-by-step log of what the agent is doing (its “thoughts” or plan and the actions).
3. **Agent Actions:** The agent has a set of tools at its disposal ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=Agent%20has%20access%20to%20multiple,tools%2C%20including)):
   - It can **read** files (it will show the content of files it opens in the log).
   - It can **write** to files (applying edits and showing diffs).
   - It can **search** your codebase (like grepping for a term).
   - It can **run terminal commands** (the output of the command will be shown) – for example, running your test command or starting a dev server.
   - It can also call external endpoints or use the Model Context Protocol (an advanced feature for calling other AI services) ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=,Run%20terminal%20commands)), though that’s behind-the-scenes.
4. **Monitoring and Intervening:** You will see messages like “Agent: Reading file X”, “Agent: Writing changes to Y”, “Agent: Running `npm test`” along with any results (like test output). The agent will reason about the results. For example, if tests fail, it might decide to fix an issue and try again. The Agent can take up to 25 such actions in a sequence on its own before stopping ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=it%20can%20perform%20many%20consecutive,actions%20without%20much%20supervision)). At any point, you can pause or stop the agent if it’s doing something undesired.
5. **Review Final Changes:** Once the agent believes it has completed the task (or hits the action limit), it will present the final set of changes. You then review diffs just as in normal mode and accept or reject. If the agent ran commands (like tests), you should see their outcome to judge if the result is correct.
6. **Continue if Needed:** If the agent stops after 25 steps and hasn’t finished, you might get a message like “Tool limit reached, please ask to continue.” You can simply prompt the agent again (or press a continue button if provided) to resume from where it left off ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=it%20can%20perform%20many%20consecutive,actions%20without%20much%20supervision)). You could also give additional instructions if it got something wrong.

**Example of Agent in action:** Suppose you prompt it to “add caching to all API calls in this project.” The agent might:
- Search for “http.get” or relevant patterns in the codebase.
- Open each file with API calls, insert caching logic, save them.
- Maybe modify `requirements.txt` or `package.json` to add a caching library.
- Run the project’s tests or a specific script to ensure nothing broke.
- If a test fails, it analyzes the failure, fixes the code, and retests.
- Finally, present changes for your approval.

Throughout this, the agent is effectively doing what a developer might do by hand, guided by your high-level request. This mode can save a lot of time for tedious multi-file or multi-step changes. However, it is also riskier if not watched: the agent might misunderstand something or overshoot. **Always supervise agent actions.** The interface allows you to see each step, so you have the opportunity to stop it if it’s going astray (for example, if it’s editing files you didn’t intend to change).

Agent mode currently works best with more capable models that can handle long reasoning and large context (like GPT-4 or Claude). If you’re on the free tier with only GPT-3.5, the agent might be limited. On Cursor Pro, the agent will typically use the best model available for the task (often GPT-4 by default, because complex tasks need its reasoning ability).

In summary, use Agent mode for **complex refactoring, codebase-wide changes, or when you want the AI to autonomously figure out the steps**. Use Normal mode for simpler, one-shot changes. In either case, Cursor keeps you “in the loop” by showing diffs and letting you confirm changes, so you maintain control over your codebase ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Agent)).

*(Note: Agent mode is a powerful feature that may still be under active development. Expect it to improve, and always keep version control backups – just as you would when using any automated refactoring tool – so you can revert if something goes wrong.)*

## Advanced Features

Beyond the basics, Cursor AI provides several advanced capabilities to enhance your development workflow. These features are especially useful in larger projects or specialized scenarios:

### Documentation Integration (`@Docs`)

Keeping documentation at your fingertips can greatly improve development speed. Cursor allows you to integrate external documentation directly into the editor, so the AI can reference official docs or guides when assisting you. 

There are two main ways documentation is handled:

- **Built-in Library Docs:** Cursor comes with a set of popular third-party libraries and frameworks pre-indexed (for example, React, Node.js, Python’s standard library, etc.). You can reference these by typing `@LibraryName`. For instance, `@React` or `@NumPy` might pull up the relevant documentation snippet for that library ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Use%20Documentation)).
- **Custom Documentation:** You can add your own documentation sources. In **Settings > Features > Docs**, there is an option to **“Add new doc”** ([Exploring Cursor: Accessing External Documentation using @Doc](https://www.rudrank.com/exploring-cursor-accessing-external-documentation-using-doc/#:~:text=Setting%20Up%20Docs%20in%20Cursor)). Here, you can provide a URL or documentation site, and Cursor will crawl and index it. For example, you might add the URL to your company’s internal API docs, or a specific open-source library documentation that you use.

Once a documentation source is added and indexed, using it is simple. In chat or composer prompts, invoke it with `@Docs` followed by a search query or select it from the @ menu. You can also just mention the doc by name if it's unique. For example: *“@Docs Django QuerySet filter usage”* might retrieve the section of Django’s documentation about QuerySet filtering. Or if you added internal docs named “MyAPI”, you could ask: *“According to @MyAPI, what parameters does the `loginUser` endpoint accept?”* – the AI will use the integrated documentation to answer.

This integration means the AI’s answers can be more accurate and up-to-date, since it’s not relying solely on its trained knowledge (which might be outdated). It’s especially useful for technology that evolves fast or any proprietary frameworks that the base AI wouldn’t know about.

**Setup Example:** Suppose you want Cursor to help with AWS SDK for JavaScript, and you have the official AWS docs link. Go to settings, add the AWS SDK docs URL as a new doc. Once it finishes indexing (it might take a minute), you can ask in chat: *“@Docs AWS.S3 How do I upload a file to S3 with public-read access?”* The AI will fetch the relevant part of the AWS documentation and include it in its answer, giving you code that likely matches the official recommendations ([Exploring Cursor: Accessing External Documentation using @Doc](https://www.rudrank.com/exploring-cursor-accessing-external-documentation-using-doc/#:~:text=Cursor%20lets%20you%20add%20external,or%20mentioning%20the%20document%27s%20name)) ([Exploring Cursor: Accessing External Documentation using @Doc](https://www.rudrank.com/exploring-cursor-accessing-external-documentation-using-doc/#:~:text=Cursor%20lets%20you%20add%20external,or%20mentioning%20the%20document%27s%20name)).

Keep in mind that large documentation sites can be heavy; add only what you need. Also, the documentation is stored locally/indexed for context – you don’t need internet after adding it, except to update it. If docs change, you can re-index or remove/re-add them.

Using `@Docs` within Cursor ensures you *stay in flow*: no swapping to a browser to search docs, copying code, etc. Everything happens in one place. This makes Cursor not just an AI coder, but a documentation browser as well.

### Browsing the Web with `@Web`

Sometimes you need information that isn’t in your code or docs – for example, an error message explanation from StackOverflow, or the latest usage of a library that just got released. Cursor’s `@Web` feature lets the AI search the internet on your behalf and pull in relevant information ([Exploring Cursor: Browsing the Web for Resources using @Web](https://www.rudrank.com/exploring-cursor-browsing-web-for-swiftui-documentation/#:~:text=that%20Cursor%20can%20browse%20the,web%20directly)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Ask%20the%20Web)).

To use it, simply include `@Web` in your prompt followed by a query. For example:

- *“@Web search ‘TypeError cannot read property push of undefined’”* – The AI will perform a web search for that error, likely find a StackOverflow page or blog, and then summarize the cause and solution in its answer.
- *“@Web find the current weather in Tokyo”* – This is more general; the AI might fetch from a weather site. (Keep in mind the AI might not have real-time info depending on how `@Web` is implemented, but it can fetch static information from the web.)
- *“@Web Python 3.12 release notes – what changed in the `asyncio` library?”* – The AI will look up the Python 3.12 release notes page, read the part about `asyncio`, and relay the information.

Under the hood, `@Web` triggers Cursor to use a search engine or web API. The results (webpages) are then processed by the AI. The AI doesn’t return the entire webpage; it will extract the parts likely to answer your question and incorporate them into its response.

**Important considerations:**

- **Browsing Limits:** The web feature is subject to some limits for fairness and to avoid abuse. It may not work for very broad queries or might sometimes say it cannot find info if the query is too generic.
- **Real-time Data:** Cursor is not guaranteed to fetch real-time data like an API call (e.g., actual stock prices or current time) unless that info is readily available on a page. It’s mainly for documentation, forum answers, and text content from the web.
- **Safety and Relevance:** The AI will try to pull only relevant info, but it’s still wise to verify critical information from official sources. Use the web feature as a quick lookup, but if it’s a complex issue (like a particular stack trace), you might still want to read the full discussion it came from for more context.

By using `@Web`, you reduce the need to Alt-Tab to a browser. For example, if you get a complex error from a library, you can ask Cursor to search it; often it will surface an explanation or solution that was posted online ([Exploring Cursor: Browsing the Web for Resources using @Web](https://www.rudrank.com/exploring-cursor-browsing-web-for-swiftui-documentation/#:~:text=He%20mentioned%20that%20Cursor%20has,between%20apps%2C%20this%20sounded%20amazing)) ([Exploring Cursor: Browsing the Web for Resources using @Web](https://www.rudrank.com/exploring-cursor-browsing-web-for-swiftui-documentation/#:~:text=Using%20%40web%20to%20Fetch%20the,iOS%2018%20Zoom%20Transition%20API)). This keeps your focus in the editor and can speed up debugging significantly.

*(If `@Web` ever fails or says it cannot find something, ensure you have an internet connection. Also note that as of 2025, the web feature is improving; some queries might not be handled, especially if they require interacting with a website login or running scripts.)*

### Visual Diff and Merging of AI Changes

When Cursor’s AI makes changes to your code – whether via Chat suggestions or the Composer – it provides a **visual diff** interface for you to review those changes before they go into your files. This is a crucial feature that gives you, the developer, final say and oversight on AI contributions.

After the AI generates output that affects your files, you will typically see a diff view: additions are highlighted (often in green), deletions in red, modifications side-by-side or inline similar to a Git diff. This happens in multiple scenarios:

- **Applying a Chat Suggestion:** If you click “apply” on a chat code block answer, Cursor will show the changes that will be made rather than immediately modifying the file. You can confirm the diff looks correct, then accept ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Instant%20Apply)).
- **Composer Results:** In both Normal and Agent mode, after the AI prepares changes, the Composer will present diffs for each file it wants to create or change ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=When%20Composer%20suggests%20changes%3A)). You can navigate through them, and each has accept/reject options.
- **Inline Prompt Changes:** If using the inline Cmd+K prompt on a selection, the suggested modification might be shown inline with edits marked, which you then approve.

This visual diff review is similar to a code review but done instantly with the AI’s output. **Always take a moment to read through the diff.** This helps catch any misunderstandings the AI had. For example, maybe it removed a line you didn’t intend to remove or renamed a variable inconsistently. You can often spot these in the diff.

**Selective Merging:** In the diff view, you are not forced into all-or-nothing. You can accept some changes and not others. One way is to manually edit in the diff view – it’s not just read-only; you can tweak the AI’s changes before finalizing. Alternatively, you might accept the whole diff and then make your own edits afterwards. If the diff spans multiple files, you typically accept them file by file.

**Checkpoints:** Cursor implements a checkpoint system in the Composer for multi-step sessions ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=Checkpoints)). Every time the AI makes an iteration of changes, it marks the state. You can see a list of checkpoints in the Composer panel. If you accept changes and then decide it wasn’t what you wanted, you can revert to a previous checkpoint (essentially undoing all changes back to an earlier state). This is like an automatic backup at each AI edit step. It’s very handy if an Agent goes down a wrong path; you can roll back and try a different approach.

**Visual Diff Example:** Suppose you asked to add logging to all functions. The AI modifies 5 files. The diff view will show each file with additions (e.g., lines where `logger.info(...)` was added). You might notice in one file that it added an import for the logger that’s not needed because it was already imported. You can remove that duplicate import in the diff. Then accept all changes. Now the code applied is exactly as you want. Without the diff, the AI might have introduced a minor duplication; with the diff, you caught it before it even hit your code.

In summary, the visual diff and merging interface ensures AI changes are transparent and reviewable. This fosters trust – you see exactly what’s going to happen – and it prevents accidents. It’s a safety net that we strongly encourage using; never blindly apply changes without at least a quick scan. Treat AI suggestions like pull requests from a teammate: review them, test them, and only then merge ([Cursor – Composer](https://docs.cursor.com/composer#:~:text=When%20Composer%20suggests%20changes%3A)). Cursor makes that process easy and fast.

### Rule Debugger (Testing AI Rules)

When using Cursor’s AI Rules (see the next section on customization), you might want to verify that they work as intended. The **Rule Debugger** is a conceptual tool or methodology to test and troubleshoot your rules.

*(Note: The Rule Debugger is an emerging feature; if it’s not directly in the UI yet, these steps can be done manually to simulate it.)*

**Why you need it:** Suppose you wrote a project rule that says “In SQL files, the AI should never use SELECT * in queries.” You want to be sure this rule is actually active, and see how the AI behaves with and without it.

**How to use Rule Debugging:**

- **Isolate a Scenario:** Create a prompt that would trigger the rule. In this example, you might open a `.sql` file and ask the chat, *“Write a query to get all columns from the Users table.”* Normally, the AI might produce `SELECT * FROM Users;`. With your rule, you expect it to avoid `*` and instead list columns.
- **Run with Rule On:** Ensure your rule file for SQL is in place. Ask the AI (in chat or composer) the question. Observe the output. Does it follow the rule? (E.g., does it list columns explicitly?)
- **Run with Rule Off:** To confirm the rule’s effect, temporarily disable the rule and ask the same question again. You can disable a rule by renaming the file (e.g., add `.off` extension) or moving it out of `.cursor/rules` momentarily. Then ask the question anew. If the AI now gives a different answer (like using `SELECT *` when the rule was off), you have evidence that the rule works. Remember to put the rule file back afterwards.
- **Use System Messages:** In some cases, Cursor might offer a console or log where it states which rules were applied to a given request. Check the Developer Tools console (`Help > Toggle Developer Tools` in the menu) for any debug logs. The Rule Debugger might surface info such as “Applied rules: sql_guidelines.md, naming_conventions.md” when you make a prompt. This can confirm that your rule file was recognized.
- **Adjust and Retry:** If you find the rule didn’t apply, the debugger approach helps pinpoint why. Maybe the file pattern didn’t match (your file is `.sql` but you named the rule for `.psql` files, for instance). Maybe the rule text wasn’t clear enough. Tweak the rule and test again.

**Troubleshooting with Rule Debugger:**

- If a rule isn’t being picked up, check the **Rules** section in Cursor’s settings to see if global rules are overriding it. The debugger might show both global and project rules being applied.
- If the AI is doing something unexpected, use the Rule Debugger approach by crafting a minimal prompt that highlights the behavior. For example, if you have a rule “explain code with comments,” but the AI isn’t doing it, ask the AI explicitly in chat *“Are you aware of any rules about comments?”* – it might actually list the rules (since those are part of its system context) or explain its reasoning, which could clue you in if the rule was misinterpreted or ignored.
- The Rule Debugger can also simply be *you using the AI to analyze the rules.* You could open a rule file and ask the chat, *“Do the following rules conflict or cause any issue?”* The AI might itself point out if two rules are contradictory. This meta-use of AI can be surprisingly helpful.

In essence, the Rule Debugger is about verifying your AI rules in practice. By testing scenarios and checking which rules are active, you ensure that your customization of Cursor’s behavior is effective. This saves time in the long run – you don’t want to assume a rule is guiding the AI, only to find out later it wasn’t loaded at all.

*(As Cursor evolves, a dedicated Rule Debugger interface may be introduced, making this process more straightforward. For now, these manual strategies achieve the goal.)*

### Multi-Model Consensus

Cursor can utilize multiple AI models to collaborate on answers, a cutting-edge feature aimed at improving solution quality and reliability. In a multi-model setup, two (or more) different models can weigh in on your prompt, and Cursor will reconcile their outputs or have them verify each other’s work.

**How it works (Conceptual):** Imagine you have both GPT-4 and Claude available. When you ask a complex question or request a code generation, Cursor might prompt both models in parallel. It then compares the answers:
- If the answers agree, that consensus is likely a correct or at least safe solution.
- If they differ, Cursor can either choose the one that seems better, or even present you with both perspectives (perhaps highlighting differences).

Another approach is a staged one: one model generates an answer, and another model reviews it. For instance, GPT-4 writes a function, and Claude checks that function for bugs or adherence to requirements, then the feedback is used to improve the code. This way, you benefit from the strengths of each model (maybe one is more creative, another more detail-oriented).

**User Experience:** Currently, multi-model consensus might not be exposed as a big obvious button (depending on Cursor’s latest version), but here’s how you might leverage it:
- **Ask for verification:** After getting an answer from one model, you can manually switch models and ask, *“ModelB, do you agree with the above solution? Can you improve it?”* This is a manual way to do multi-model collaboration – you are orchestrating it.
- **Automatic consensus (Pro feature):** Cursor Pro may introduce an option where certain prompts automatically use more than one model. For example, when Agent mode runs a complex task, it might internally use one model to plan and another to execute. From your perspective, you just get a more reliable outcome. (The details of this are mostly under the hood.)
- **Consensus Feedback:** You might see in some outputs a note like “(Verified by another model)” or the AI might say, “I double-checked this solution for errors.” This indicates consensus logic was applied.

**Benefits:**
- **Accuracy:** Two models agreeing on a piece of code gives more confidence that it’s correct. If one model misses an edge case, perhaps the other catches it.
- **Reduced Biases:** Different models have different “styles” and may catch different issues. By combining them, Cursor mitigates individual model quirks.
- **Creative vs Critical:** One model can generate creative approaches, another can critique. For example, one writes a complex algorithm, another points out a simpler approach or a potential bug.

**Example:** You ask Cursor to implement a complicated algorithm. Cursor uses GPT-4 and Claude. GPT-4 produces an implementation. Claude then reviews and says, “I think this part could be off-by-one, and it doesn’t handle empty input.” Cursor then refines the solution to address those points and presents you the improved code. All you see is the final result with perhaps a comment that it was verified by Claude. This saves you from discovering the off-by-one error later in testing.

As of early 2025, multi-model consensus is an emerging feature in AI coding assistants. Cursor’s approach is to **keep the programmer in the loop** (so any consensus check is an aid, not a silent override of what you asked) while harnessing multiple models when available to deliver the best possible outcome. It’s like having two code reviewers instead of one.

*(Availability: Using multiple models obviously requires access to them. This feature is most useful to Pro or Enterprise users who can utilize GPT-4, Claude, etc., simultaneously. Free users with only one model won’t see a benefit here. Also, consensus might make responses a bit slower since it’s doing extra work, but the improvement in quality can be worth it.)*

### Security and Privacy Features

When integrating an AI into your development process, it’s important to understand how your code and data are handled. Cursor includes several security and privacy mechanisms to protect your source code and sensitive information:

- **Privacy Mode:** Cursor offers a Privacy Mode setting that you can enable during setup or in settings at any time. When Privacy Mode is **on**, Cursor guarantees that none of your code is stored on its servers in plaintext after processing ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=Privacy%20Mode%20Guarantee)). In other words, the code is sent to the AI models to generate responses, but not logged or kept for training. This mode is crucial for proprietary codebases. In fact, about half of Cursor users enable Privacy Mode, underscoring its importance ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=match%20at%20L415%20We%20take,guarantee%20in%20our%20Privacy%20Policy)). (If Privacy Mode is off, Cursor might cache some data to improve performance, but even then, they have agreements like zero-retention with their AI providers to not use your data ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=)).)
- **Data Encryption:** All communications between Cursor and the cloud services (like model APIs) are encrypted over HTTPS. This means your code and prompts are protected in transit. Cursor relies on secure infrastructure (primarily AWS) for its services ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=%3A)).
- **SOC 2 Compliance:** Cursor is SOC 2 Type II certified ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=Certifications%20and%20Third)), meaning it has undergone third-party audits to ensure it meets strict security standards in how it handles data and system operations. Enterprises can request the report for their own compliance checks.
- **Local Code Indexing:** The code indexing (for enabling codebase Q&A) is done on your machine first – Cursor chunks and embeds your code locally, then sends the numerical embeddings to its server for searching ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=For%20better%20and%20more%20accurate,accuracy%20of%20your%20codebase%20answers)). Those embeddings are a transformed representation of your code, not raw code, and they are used only to fetch relevant context. If Privacy Mode is on, even those embeddings are not stored long-term tied to your identity.
- **Ignoring Sensitive Files:** Use of `.gitignore` and `.cursorignore` is not just for performance – it’s also a way to exclude files with secrets or personal data from being sent to the AI ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Cursor%20uses%20the%20same%20package,committing%20it%20to%20the%20repository)). For instance, you might add `.env` or `secrets.yml` to `.cursorignore`. Cursor will then refrain from including those in any context it sends. Always review your ignore settings to cover any files that should remain private.
- **On-Premises and Self-Hosting:** For organizations that cannot allow any cloud access, Cursor has (or is developing) enterprise solutions. This might include the ability to deploy a local server that runs the AI models on-premises, or a proxy that keeps all data within a VPC. If you work in a highly regulated environment, reach out to Cursor’s enterprise sales to discuss options. The team is aware that some users will need offline or self-hosted versions, and security is a top priority ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=While%20we%20have%20several%20large,make%20a%20proper%20risk%20assessment)) ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=that%20we%20are%20still%20in,make%20a%20proper%20risk%20assessment)).
- **User Authentication and Accounts:** Cursor ties your usage to an account for licensing and syncing settings. They implement standard authentication security. Be sure to use a strong password or secure OAuth (like GitHub login) and enable 2FA on your accounts where possible. This protects your AI usage from being hijacked or abused by someone else.
- **Vulnerability Reporting:** Cursor has a policy for vulnerability disclosure ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=Keeping%20your%20source%20code%20and,we%20approach%20security%20for%20Cursor)). If you ever find a security bug in the tool, you can report it (for example, via their GitHub Security page or email) and they are responsive in addressing issues.

**Practically speaking:** if you are using Cursor on a closed-source codebase at work, turn on Privacy Mode and double-check your ignore files to exclude any highly sensitive material. This way, you leverage the AI while minimizing data exposure. Also, treat the AI like an intern: *do not share credentials or keys with it in prompts*, and avoid asking it to generate secrets. Even though the data isn’t stored, it’s just good practice not to feed credentials anywhere they don’t need to be.

In summary, Cursor’s design acknowledges the sensitivity of source code. By providing Privacy Mode and respecting ignore rules, it allows developers in even security-conscious environments to use AI assistance with more peace of mind ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=We%20depend%20on%20the%20following,see%20%209%20section)) ([Cursor – Ignore Files](https://docs.cursor.com/context/ignore-files#:~:text=To%20ignore%20files%20from%20being,works%20for%20git)). Always stay informed by reading their security page for the latest updates on how your data is handled.

## Working with Projects

Cursor is particularly powerful when working on real projects (as opposed to small single-file scripts) because it can take into account the broader context of your codebase. Here we cover how to effectively use Cursor in the context of a project repository, including indexing, ignoring files, and handling large monorepos.

### Codebase Indexing for Context

**What is Codebase Indexing?** When you open a folder (project) in Cursor, it can **index your codebase** to create embeddings that the AI uses for context ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Index%20your%20Codebase)). Essentially, it preprocesses your files so that later, if you ask a question about your code, it can quickly look up relevant pieces instead of scanning everything in real-time. Indexing improves both the speed and accuracy of code-related answers.

You can control indexing in **Cursor Settings > Features > Codebase Indexing**. There, you can see if indexing is enabled and the status (how many files indexed, etc.) ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=your%20workspace%20to%20keep%20your,personal%20codebase%20context%20current)). When you first open a project, Cursor might automatically start indexing (unless you turned off auto-index in settings). You’ll typically see a progress indicator.

**Using Indexed Context:** Once indexing is done, you can do things like:

- Ask in chat: *“Where is the function `calculateInvoice` used in this project?”* – The AI will use the index to find references across files and answer (it might say “It’s used in Billing.py line 120 and in ReportGenerator.js line 55,” etc.).
- Use the `@codebase` reference in a prompt to have Cursor consider the whole project. For instance: *“@codebase What are the major modules of this application and how do they interact?”* – This broad query causes the AI to draw from an overview of the codebase structure.
- In the background, features like **Codebase Q&A** (asking questions about code) and some autocompletions utilize the index. It makes Cursor “aware” of things across files, like class names, function definitions, usage examples, etc., which it can bring into suggestions ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Codebase%20Answers)).

**Local and Personal:** The codebase index is stored per user. If you and a colleague both index the same repo, each of you has your own index on Cursor’s servers tied to your accounts. If you update your code (pull new changes), Cursor will update the index incrementally. The index is not shared unless you share your account, so no one else can query your indexed data directly.

**When to Re-index:** Cursor usually keeps the index updated automatically as you edit or add files. However, if you do a massive change (like switching branches or pulling a big update), and the AI responses seem off, you might manually trigger a re-index from the settings to refresh everything. Also, if you ever suspect some files were missed, check the index settings where you can see a list of ignored files and possibly which were indexed.

*(One limitation: binary or very large files are generally skipped from indexing. Cursor focuses on code and text. So if your project has a huge 5MB JSON, it might ignore it by default to save space unless you query it directly.)*

### Using `.cursorignore` to Exclude Files

Not all files in a project are useful for the AI’s context. Build artifacts, dependencies, large datasets, or generated code can confuse the AI or slow down indexing. To manage this, Cursor uses an ignore mechanism similar to Git’s. 

- You can create a **`.cursorignore`** file in your project’s root directory to specify files and folders that Cursor should ignore during indexing ([Cursor – Ignore Files](https://docs.cursor.com/context/ignore-files#:~:text=About%20)).
- The syntax of `.cursorignore` is exactly like a `.gitignore`: you list patterns for files or directories. For example:
  ```
  node_modules/
  *.min.js
  secrets.yaml
  ```
  This would ignore the `node_modules` folder, any `.min.js` file, and a specific secrets file.
- **Automatic Gitignore Respect:** Importantly, Cursor automatically respects your `.gitignore` settings ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Cursor%20uses%20the%20same%20package,avoid%20committing%20it%20to%20the)). That means any patterns in `.gitignore` are treated as if they’re in `.cursorignore` too. If your repo already ignores `node_modules` or `dist/`, Cursor will also ignore those by default when indexing ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Cursor%20uses%20the%20same%20package,avoid%20committing%20it%20to%20the)). This is great because it usually covers the common cases of excluding libraries or outputs.
- **Combining Rules:** You can use both `.gitignore` and `.cursorignore`. A best practice is to put personal or AI-specific ignores in `.cursorignore` (and add `.cursorignore` itself to your `.gitignore` so it’s not committed) ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Cursor%20uses%20the%20same%20package,avoid%20committing%20it%20to%20the)). For instance, if you temporarily want to exclude a certain subfolder from AI consideration, you add it to `.cursorignore` locally without changing the team’s `.gitignore`.

**Why ignore?** Excluding irrelevant files makes the AI’s job easier and responses more accurate. If you don’t ignore, say, your `vendor/` or `third_party/` libraries, the AI index might get bloated with code you never want to ask about or have included (and it could even mistakenly use that in suggestions). By ignoring them, the AI focuses only on your code.

**Runtime Effects:** The ignore rules mainly affect indexing (and the special codebase queries). The **Chat and Composer** currently can still access ignored files if you explicitly ask about them or open them ([Cursor – Ignore Files](https://docs.cursor.com/context/ignore-files#:~:text=Chat%20and%20Composer%20Context)). For example, if `config.php` is in .cursorignore but you open it and ask the AI about it, it will read it because you gave direct context. The ignore is to avoid *automatic* inclusion. Think of it as controlling the knowledge base of the AI, not a security feature (don’t rely on it to hide secrets – though you should still ignore secret files to avoid accidental inclusion).

**Example `.cursorignore`:** 
```
# Ignore build artifacts
/out/
*.o
*.class

# Ignore test snapshots
tests/__snapshots__

# Ignore large data
data/*.csv
```
With this, when Cursor indexes, it will skip any `out` directory, any compiled object or class files, the test snapshots directory, and all CSV files in the data folder. As a result, queries about the code won’t be distracted by binary content or massive data, and the embedding storage is used only for relevant code.

Keep your ignore file updated as your project grows. Whenever you add a new dependency folder or some cache files, consider adding them to `.cursorignore`. This keeps Cursor’s context clean. You can always temporarily remove an entry if you do need the AI to look at something in there.

### Working with Large Monorepos

Many organizations use monorepos – a single repository that might contain dozens of projects, services, or packages. These can be **huge**, with hundreds of thousands of files. Using Cursor on a monorepo is possible and can be beneficial (because the AI can see cross-project patterns), but it requires strategical setup:

- **Strategic Indexing:** It’s usually neither necessary nor efficient to index an entire monorepo. Focus on the parts of the codebase relevant to your current task. For example, if you work on the “frontend” directory only, you can ignore the “backend” directory and vice versa. As mentioned, each developer can maintain their own `.cursorignore` to exclude the sections they don’t work on ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=When%20working%20with%20large%20monorepos,strategic%20about%20what%20gets%20indexed)). This way your index stays smaller and more pertinent to you.
- **Add to Gitignore:** Monorepos are typically shared by many. You don’t want your personal ignore preferences to accidentally get committed. It’s a good practice to add `.cursorignore` to the root `.gitignore` of the monorepo ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=,gitignore)) (if policy allows). This signals that these files are meant to be local. If that’s not possible, be careful not to commit your `.cursorignore`.
- **Partial Open:** Cursor (like VS Code) allows opening a subfolder as the root workspace. If the monorepo is too unwieldy, you can just open the sub-directory you care about. For example, open `repo/frontend/` as your project in Cursor rather than the whole repo. Cursor will then treat that as the root and index only within it. This can drastically reduce noise. The downside is it won’t automatically see references outside that folder, but you can always open the needed file manually or use `@Web` to fetch if needed.
- **Model Context Limits:** Even if you did index everything, keep in mind the AI still has a finite context window. It won’t dump the entire monorepo into an answer. It will fetch the top relevant pieces. So having an enormous index doesn’t mean the AI sees “all code at once” – it means it has more to search from. This can be powerful (e.g., finding a usage anywhere in a huge codebase), but it can also slow down query time slightly. Monitor the performance; if answers become slow, consider narrowing the index.
- **Collaborative Filtering:** If you are in a team setting with a monorepo, each team member might maintain similar ignore files. It could be useful to share a recommended `.cursorignore` template for the repo (without forcing it in git). For instance, front-end devs share one that ignores `backend/`, and back-end devs ignore `frontend/` and so on. Consistency can help if you share prompt tricks or rules, as the AI will have similar context assumptions for everyone.

**Example scenario:** A monorepo has 5 major projects. You work on Project A. You set your Cursor to ignore Projects B-E entirely. Now, when you ask something like “find all TODO comments,” Cursor will only search Project A (faster, and you’re not distracted by irrelevant TODOs elsewhere). If one day you need something from Project B, you can either remove it from ignore temporarily or open that folder separately. This approach keeps the AI focused and efficient.

The Cursor docs emphasize being *strategic* with large repos ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=Working%20with%20large%20monorepos)), and user experiences concur: a bit of upfront tailoring of the index can make a huge difference in usability. Large codebases are where AI assistance shines (who can remember everything in 100k lines of code?), but also where you must harness it carefully. Use the tools (ignore files, targeted indexing) to make Cursor your helpful guide through the monorepo jungle, rather than overwhelming it with the whole forest at once.

### Best Practices for Large Projects

Some general tips when using Cursor on sizable projects or in professional environments:

- **Combine AI and Unit Tests:** If you have a test suite, run it after accepting AI changes. Cursor’s suggestions are usually correct, but in a large codebase, even a small error can have ripple effects. Running tests will catch anything the AI might have missed. In agent mode, you can even have the AI run tests for you as part of the plan, and react to failures.
- **Iterate in Sections:** Don’t ask the AI to do an extremely broad refactor all at once on a huge project. Break it down. It’s better to do “Convert module X from library A to library B” first, then do the next module, than “Convert entire codebase from A to B” in one go. Smaller prompts make it easier to spot issues in diffs and isolate problems.
- **Use Global Rules for Consistency:** In a large project, consistency is key. If you have certain patterns to enforce (error handling style, logging format, etc.), use global or project rules so the AI follows them everywhere. This saves you from manually correcting the same style issue in multiple places.
- **Leverage Chat for Architecture Questions:** On a big project, it might be hard to know where something is implemented. Don’t hesitate to ask Cursor, *“Which file handles user authentication?”* or *“Summarize how data flows from the UI to the database.”* If indexed, it can often outline the architecture for you, or at least give pointers. This is a productivity boost when onboarding to a new large codebase.
- **Resource Consideration:** Big projects mean more tokens for the AI to chew on. If you’re on an API usage plan, be mindful of how often you query huge contexts (like @codebase queries). Focused questions are not just better for answers but also cheaper in terms of token usage.
- **Fallback to Traditional Tools when Needed:** Cursor is great, but for certain tasks, also rely on your usual tools. Grep the codebase if you suspect the AI missed something simple, or use your build warnings. The AI augments your work; it doesn’t replace understanding your code. Treat it as a knowledgeable assistant, not an all-knowing oracle.

By following these practices, you can make Cursor an integral part of working with complex projects, helping you navigate and modify the code with confidence and efficiency.

## Customizing AI Behavior with Rules

Every codebase and developer has a unique style and set of guidelines. Cursor’s **Rules for AI** feature allows you to encode these preferences so that the AI assistant follows them. Think of rules as a way to give the AI its own “coding standards manual” for your projects.

### What are Cursor AI Rules?

AI rules are configuration snippets that shape how the AI responds. They can **instruct the AI on style, best practices, architectural patterns, or anything you want it to keep in mind** ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Using%20rules%20in%20Cursor%20you,a%20system%20prompt%20for%20LLMs)). For example, you might have a rule that says “Always write SQL keywords in uppercase,” or “In this project, prefer functional components over classes (for React).”

There are two types of rules, as mentioned earlier:

- **Global Rules:** These apply to all projects for your Cursor installation. You set them in your **Cursor Settings > General > Rules for AI** section ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Global%20Rules)) ([Mastering Cursor Rules: A Developer's Guide to Smart AI Integration - DEV Community](https://dev.to/dpaluy/mastering-cursor-rules-a-developers-guide-to-smart-ai-integration-1k65#:~:text=1)). Global rules are good for personal preferences that you want no matter what you’re coding. For instance, you might globally instruct the AI to write comments in English, or to avoid using certain slang or insecure functions.
- **Project-Specific Rules:** These live inside your project in a folder named `.cursor/rules/` (note, this is a directory, not a single file) ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Project%20rules%20offer%20a%20powerful,different%20parts%20of%20your%20project)). Project rules are further broken down by file patterns or contexts. Each rule is typically a markdown file (with extension `.md` or `.mdc`) containing instructions. You can have multiple files, each targeting different parts of the codebase.

**How Project Rules Work:** In the `.cursor/rules` directory, you can create files like `frontend.mdc`, `*.mdc` etc. The content of a rule file can include a description (optional) of when to apply it, pattern globs for files, and the actual instructions for the AI ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=Here%E2%80%99s%20how%20they%20work)). Cursor will automatically consider these rules whenever the AI is working with matching files. For example, if you have a rule file that specifies it applies to `**/*.sql` files and contains guidelines for SQL, whenever you ask something related to a `.sql` file or the AI is about to generate SQL code, it will include those guidelines in the prompt it sends to the model.

**Example Rule File (`.cursor/rules/sql_style.md`):**
```markdown
Description: Guidelines for SQL queries in this project
Patterns: **/*.sql

- **No SELECT \***: Always specify column names in SELECT queries.
- **Use Prepared Statements**: Do not concatenate strings to form SQL. Use parameters.
- **Uppercase Keywords**: Write SQL keywords (SELECT, INSERT, WHERE, etc.) in uppercase.
```
This is a human-friendly way to state rules. The AI will interpret it appropriately. So if you ask the AI to generate a query, it will follow these rules (e.g., it will not use `SELECT *` because the rule says not to).

**Applying and Organizing Rules:** You might have multiple rule files:
- `frontend.mdc` for rules about front-end code,
- `security.mdc` for security-related rules (like “sanitize user input always”),
- `naming.mdc` for naming conventions (“use camelCase for variables”, etc.),
- etc.

You can also have subfolders inside `.cursor/rules`. For example, you could organize by language or feature: `./.cursor/rules/python/style.md` and `./.cursor/rules/python/performance.md`. The structure is up to you; what matters is patterns and content.

Cursor will attempt to match the best rules for a given context. If you reference a specific file in a prompt, it includes rules whose pattern match that file. If you just ask generally while in a certain file, it likely includes the rules for that file type.

**Priority:** If both global and project rules apply, typically project rules should take precedence for that project (since they are more specific). However, if there is no conflict, all applicable rules are combined. If there is a direct conflict (global says one thing, project says another), it’s not clearly documented which wins – so avoid conflicting rules. Usually, keep global rules high-level and non-contradictory (e.g., global: “write clear comments”, project: “comments must include JIRA ticket number if available” – these can coexist).

### Creating and Editing Rules

Cursor provides a handy way to create a new rule file: open the Command Palette (Cmd+Shift+P) and run “**New Cursor Rule**” ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=together)). It will prompt for a title or type and then create a new markdown file in `.cursor/rules` ready to edit. You can then fill in your instructions.

When editing rule files, you can use Markdown for formatting. The AI will see the raw text, not the rendered version, but formatting can help you structure the rules clearly (bullet points, bold for key terms, etc., as in the example above).

Because these files live in your project, you can commit them to your repository. This is powerful: it means your entire team, if using Cursor, shares the same AI guidance. It’s like a **living documentation** for both developers and the AI. Even developers not using Cursor can read these rule files as additional documentation of code style decisions.

*(If you prefer not to commit these files, you could add `.cursor/` to gitignore. But sharing them often benefits team consistency.)*

### Tips for Effective Rules

- **Be specific but not overly restrictive:** If you make rules too broad (“Never use recursion”), you might hamper the AI’s creativity or solutions. Focus on rules that enforce true standards or prevent known issues, but allow the AI some flexibility to solve problems.
- **Use positive instruction:** Instead of just “Don’t do X”, also consider telling it what to do. For example, “Avoid global variables. **Use dependency injection** to pass needed objects.” This way the AI knows the preferred alternative.
- **Keep rules concise:** The rules are essentially injected into the prompt. If they’re extremely long, they eat into the prompt space and might dilute importance. Summarize and use bullet points or key phrases. The AI is quite adept at understanding short directives.
- **Organize logically:** Group related rules together. Perhaps one file for styling/formatting, another for architecture, another for specific third-party APIs (e.g., “when using Library X, prefer Y over Z function”). This modular approach means the AI will only load the relevant rules based on context.
- **Test the rules:** As discussed in the Rule Debugger section, try out scenarios to see if the AI follows the rule. This will confirm if your pattern matching is correct and if the rule phrasing is effective.

### Troubleshooting Rules

Even with good rules, you may encounter situations where the AI seemingly ignores or breaks a rule:

- **Check the file pattern:** The rule only applies if the context matches. Maybe your pattern `**/*.js` didn’t catch a file with extension `.jsx`. Adjust patterns accordingly (Cursor uses glob patterns – be mindful of differences like `**/` for any subdir).
- **Is the rule active?** Look in settings under Rules for AI to see if global rules are listed, and ensure project rules are in the correct folder. The `.cursor/rules` directory is at the project root. A common mistake is placing it in, say, a submodule folder or the wrong location.
- **Conflicting rules:** If two rules contradict, the AI might follow one and not the other, or get confused. Resolve conflicts by merging rules or prioritizing one. For example, a global rule says “use British English”, a project rule says “use American English” – obviously only one can happen. In such cases, the more specific (project) should override, but to be safe, avoid this scenario.
- **Model limitations:** Some models (especially older or smaller ones) might not adhere to rules as well as others. GPT-4 tends to follow rules more accurately than GPT-3.5, for instance. If a rule is critical and you notice it’s not followed with a certain model, consider using a stronger model for those tasks.
- **Complex rules:** If you put very complex instructions or multi-part formatting rules, there’s a chance the model only partially follows. Try splitting into simpler bullet points. For example, instead of a long paragraph of how to format an API response, break it into steps or examples.
- **Use comments in rules:** You can add comments or notes in a rule file if needed (maybe as HTML comments `<!-- -->` or a section the AI can ignore). But generally, whatever text is in the rule file might be seen by the model. If you need to clarify something for human readers of the rule file that you don’t need the AI to act on, you might mark it as a comment.

AI Rules essentially let you **steer the AI’s coding style**. This turns the AI from a generic assistant into one that is customized for *your* project. It’s one of Cursor’s standout features compared to simpler AI coding tools. By investing some time to write good rules, you reap the benefit in every AI interaction thereafter – the code will more likely meet your expectations on the first try, saving time in revisions.

## Troubleshooting and FAQ

Even with a smart AI assistant, you’ll encounter moments where things don’t work as expected or you have questions about usage. Below are common issues and frequently asked questions when using Cursor AI:

**Q: The AI features aren’t responding (chat is empty, no autocompletions show up). What should I do?**  
**A:** First, check your internet connection – Cursor’s AI needs to reach the server. A common cause for no response is connection issues. If your internet is fine, the next suspect is a network blocker. Are you behind a **corporate proxy or VPN**? If so, you may need to configure Cursor to use that proxy. Corporate networks sometimes block the protocols Cursor uses; for instance, Cursor’s API traffic requires HTTP/2. Some proxies (like certain versions of ZScaler) interfere with HTTP/2, causing Cursor to fail to connect ([Cursor – Common Issues](https://docs.cursor.com/troubleshooting/common-issues#:~:text=Here%20are%20the%20steps%20to,troubleshoot)) ([Cursor – Common Issues](https://docs.cursor.com/troubleshooting/common-issues#:~:text=ZScaler)). The fix in that case is to allowlist Cursor’s domains (such as `api.cursor.sh`) or adjust the proxy to permit HTTP/2. If you’re using Cursor at work, your IT department might need to assist. Additionally, ensure you haven’t exceeded any usage limits – in **Settings > Usage** you can see if you ran out of quota (for free users, there may be a daily limit on tokens or requests). If usage is the issue, the app should prompt you, but double-check. Finally, try restarting Cursor – it sounds cliché, but if the app was open for a long time, a fresh start can clear any glitchy state (and triggers re-auth if your session expired). If none of this helps, gather logs (via **Help > Toggle Developer Tools** and check Console) and reach out on the Cursor forum with details.

**Q: My codebase indexing is failing or seems stuck. How do I resolve that?**  
**A:** If indexing fails, you might see an error message or a warning like “Codebase indexing failed, falling back to slower search.” A few things to try: (1) **Restart indexing** – go to Settings > Codebase Indexing and toggle it off and on, or click reindex if available. (2) If there’s a specific file causing trouble (maybe a very large file or one with unusual encoding), exclude it via `.cursorignore` and reindex ([Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing#:~:text=If%20you%20have%20any%20large,the%20accuracy%20of%20the%20answers)). (3) Ensure you’re using a relatively recent version of Cursor; indexing issues might have been fixed in updates. (4) Check if your disk is full or if you’re low on memory – indexing can consume resources for a big project. Free up space or close other apps if needed. (5) Look at Cursor’s logs for any clues (in the Developer Tools console or log files on disk). If you see something like “embedding failed” for certain files, those might be the ones to ignore. For persistent issues, report it as a bug with your setup details (OS, project size, etc.). Meanwhile, even without a full index, you can still use chat by manually opening files; it will just be a bit slower on cross-file questions.

**Q: The AI sometimes produces incorrect code or errors. How can I trust it?**  
**A:** It’s important to remember that the AI does not guarantee correctness – it’s making educated guesses. Always review and test AI-generated code. That said, there are ways to improve trust: (1) Use the **multi-model consensus** approach if available – if two models agree on a solution, it’s more likely right. (2) Write **unit tests** (or ask the AI to write tests) for AI-generated code; then run them. The AI can even help fix any failing tests. (3) Start with smaller asks: instead of generating 500 lines at once, generate 100 and see if it runs. Iteratively build the solution with the AI. (4) Use Rules to enforce checks (for example, a rule could be “if the user asks for code, include a brief self-check or output a comment with potential pitfalls”). Ultimately, treat AI output like you would a code submission from a human junior developer: review it, run it, and don’t deploy it without understanding it. Over time, as you and Cursor develop a working rapport (with rules and context), you’ll get a feel for when you can trust it on first pass versus when to be more skeptical.

**Q: How is Cursor AI different from GitHub Copilot? Should I use both or switch?**  
**A:** Cursor and Copilot have overlapping goals but different approaches. **GitHub Copilot** integrates into editors like VS Code, providing mainly inline code completions and some conversational support (Copilot Chat). **Cursor** is its own editor, combining VS Code’s interface with deeper AI integration. Key differences ([Cursor for Developers: Ultimate Introduction](https://www.builder.io/blog/cursor-ai-for-developers#:~:text=Sure%2C%20we%27ve%20seen%20artificial%20intelligence,also%20left%20us%20wanting%20more)) ([Cursor for Developers: Ultimate Introduction](https://www.builder.io/blog/cursor-ai-for-developers#:~:text=Cursor%20is%20basically%20an%20AI,capabilities%20to%20a%20familiar%20interface)):
- *Context Size:* Cursor can utilize very large contexts (with models like Claude 100k) and index entire repositories for question-answering ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Codebase%20Answers)). Copilot’s suggestions are usually based on the file you’re in and a bit of neighboring context. If you have a question about code across multiple files, Cursor will handle it better.
- *Feature Set:* Cursor offers the Composer (with agent mode for multi-step tasks), direct web and docs integration, and customizable rules. Copilot mainly offers completion and a basic chat (in VS Code or the GitHub web). Cursor’s chat and apply workflow is more advanced in allowing multi-file edits and showing diffs.
- *Editor:* Using Cursor means using a separate application (though one that looks and feels like VS Code). Copilot lives inside your existing editor/IDE. Some people prefer not to switch editors. However, because Cursor is a VS Code fork, it supports many of the same extensions and workflows, easing the transition.
- *Cost:* Copilot is a paid subscription (~$10/month) with no free tier (aside from student benefits). Cursor currently offers a free tier with certain limitations and a Pro plan for more heavy use or better models. Depending on your usage, one might be more cost-effective. Also, Cursor’s ability to use your own API keys means you could leverage OpenAI/Anthropic billing which might be cheaper for sporadic use.
- *Open Source vs Proprietary:* Both are proprietary tools (Cursor isn’t fully open-source, though parts might be, and Copilot runs on OpenAI’s closed model). If that matters to you, there are open alternatives (but that’s another topic).
- *Using Both:* It’s technically possible to use both (e.g., use Cursor for big refactors or Q&A, and Copilot in your other IDE for quick suggestions). But they won’t share information between them. Some developers might use Copilot within something like IntelliJ or an IDE where Cursor isn’t available, and use Cursor for coding sessions where they want the deeper AI features.

In short, if you’re happy with Copilot’s lightweight assistance and strongly prefer sticking to your current editor, Copilot is fine. If you want a more robust AI partner and don’t mind (or welcome) using a VS Code-like environment, give Cursor a try – it can do a lot more in terms of interactive development. Many developers actually use Cursor alongside Copilot for a while to compare. You might start by using Cursor on personal projects or parts of the workflow (like documentation lookup and big changes) while still using Copilot day-to-day, then gradually decide which suits you better. Some have fully switched to Cursor for the richer feature set, especially when working on complex projects where the chat and agent save tons of time.

**Q: Do I need my own API keys (OpenAI/Anthropic) to use Cursor?**  
**A:** Not necessarily. By default, Cursor comes with its own backend that handles the model calls – you just use it with your Cursor account. However, Cursor does allow you to plug in your own API keys if you want ([Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai#:~:text=,Custom%20API%20Keys)). In **Settings > Custom API Keys**, you can enter keys for OpenAI or Anthropic. Why do this? One reason is if you have an API access that grants you use of models Cursor might not provide for free (for example, maybe you have an OpenAI API key with GPT-4 32k access and you want to use that context size, or you have a corporate license). Using your own key might also bypass some usage limits on Cursor’s side, since then you’re paying OpenAI/Anthropic directly for your usage. If you don’t input any keys, Cursor will use its default models based on your plan (free or pro). If you do input a key, you can select “custom” models in the model dropdown. For instance, you might see an option for “GPT-3.5 (custom key)” or similar. This feature is for advanced users who have specific needs – the majority of users do not need to worry about it. If you do use it, keep your keys safe (they’re stored locally, and sent only to the model provider). Also note, when using your own key, your data will be subject to that provider’s terms directly (Cursor’s Privacy Mode still means Cursor won’t store it, but OpenAI for example might log requests unless you have a data agreement with them).

**Q: The AI is not following my coding style. How can I improve that?**  
**A:** This is where **Cursor Rules** shine. Make sure you have set up rules reflecting your style (indentation, naming conventions, etc.). Also, lead by example: the AI often picks up style from existing code. If your project’s code is inconsistent, the AI might be confused which style to follow. In such cases, explicitly telling it in the prompt or via rules helps. You can also gently correct it in chat: *“Use camelCase for function names.”* It will usually adhere in subsequent answers. Over time, as rules are refined, you’ll see it mirror your style more closely. Another tip: if it outputs something in a style you dislike, you can ask it to convert. For example, *“Great, but please reformat that code using 4 spaces indentation and K&R braces.”* It will do so. This not only fixes that instance, but the AI also “learns” your preferences in that conversation.

**Q: I asked the agent to do a task, but it ended part-way and said to ask to continue. Why?**  
**A:** The agent has a step limit to avoid runaway processes (by default ~25 actions) ([Cursor – Agent](https://docs.cursor.com/agent#:~:text=it%20can%20perform%20many%20consecutive,actions%20without%20much%20supervision)). If a task genuinely needs more steps, you can just prompt it again with “continue” or re-run with a nudge. Sometimes the agent stops if it’s unsure or hit an unexpected obstacle (like a command failed). Check the last messages in the agent log – if it stopped due to an error, you might need to guide it. For example, if it tried to run tests but tests failed, it might pause. You should then either let it continue to fix tests or give a specific instruction like, *“Fix the failing test regarding X.”* Think of Agent as a semi-autonomous junior dev: it might need some guidance when it’s unsure. Each “continue” gives it a fresh allowance of steps.

**Q: How do I know which model is being used for what?**  
**A:** In general, the model dropdown in chat/composer shows the main model for conversation. However, under the hood, Cursor might use different models for different features. For example, it might use a fast model to generate embeddings for search, or if you highlight code and ask for an explanation, it might choose a cheaper model for a quick answer vs. a complex refactoring with GPT-4. Cursor’s **Model Context Protocol (MCP)** is an advanced system where it can route requests to specialized model endpoints ([Security | Cursor - The AI Code Editor](https://www.cursor.com/security#:~:text=)). If you’re curious, you can sometimes infer from the style of response (e.g., Claude tends to be more verbose, GPT-3.5 sometimes less detailed). Pro users might have access to model identifiers or a log. In most cases though, trust Cursor’s automation to pick the right model for sub-tasks. If you specifically want to ensure a model (like GPT-4) is used throughout, select it for your session; just note some background tasks might still use others for efficiency. The team is working on making model usage transparent while keeping it seamless.

**Q: I found a bug / have a feature request for Cursor. What should I do?**  
**A:** The Cursor community forum is the best place to report bugs or request features. There are categories for bug reports and feature requests. Before posting, you might search the forum to see if it’s already reported or requested (and upvote/comment there). When reporting a bug, include as much detail as possible: your OS, Cursor version (check *Help > About*), what you were doing, and any error messages or screenshots ([Cursor – Troubleshooting Guide](https://docs.cursor.com/troubleshooting/troubleshooting-guide#:~:text=Check%20developer%20tools%20console%20errors%3A,Look%20for%20any%20related%20errors)) ([Cursor – Troubleshooting Guide](https://docs.cursor.com/troubleshooting/troubleshooting-guide#:~:text=On%20Windows%2C%20find%20logs%20at%3A)). If it’s a UI glitch, a screenshot helps; if it’s a weird AI behavior, the prompt and response (or the rules you have, etc.) can help the developers reproduce it. For feature requests, describe your use case and why the feature would help – the team has been receptive especially if it aligns with making the AI more useful. You can also check Cursor’s changelog and roadmap to see if your issue is already being addressed. Lastly, for urgent issues (like the app not launching at all), you can reach out via Cursor’s email or Discord if available, but the forum ensures others with the same issue can see solutions.

**Q: Any tips for getting the best results from Cursor’s AI?**  
**A:** Many! To summarize a few: 
- When asking for help, **provide context**. If something is wrong, show the error message. If you want a specific approach, mention it. The more the AI has, the better.
- Use the **iterative approach**: ask, get result, refine or ask follow-up. Don’t be afraid to have a dialogue.
- **Name your composer sessions or keep notes** (Cursor has a Notepad feature via @Notepads). This helps keep track of what you’ve done in a long session.
- If the AI says something incorrect, you can highlight that and ask *“Are you sure about this part?”* Often it will reconsider and correct itself.
- **Mix and match features**: For example, if chat gives a code suggestion, apply it, then use the inline prompt (Cmd+K) on that code to refine it further. Or use @Web to fact-check an AI assertion.
- Finally, enjoy the process. Coding with an AI can feel like pair programming – engage with it naturally, and you’ll gradually learn how to get the most out of Cursor.

---

*This user guide aimed to cover all major aspects of Cursor AI as of February 2025. As the tool evolves, be sure to check the official documentation and community forums for the latest updates and tips. Happy coding with Cursor!* ([Cursor AI: A Guide With 10 Practical Examples | DataCamp](https://www.datacamp.com/tutorial/cursor-ai-code-editor#:~:text=Chat%20features)) ([Features | Cursor - The AI Code Editor](https://www.cursor.com/features#:~:text=Chat))


Okay, I'm happy to provide a complete and correctly formatted Appendix for the Cursor AI User Guide. Here it is:

---

# Appendix

## Glossary of Terms

*   **Agent Mode:** An advanced mode of the Composer where the AI can autonomously use tools (like reading/writing files, running code, and executing terminal commands) to accomplish a complex, multi-step task.
*   **Chat (Cursor Chat):** The conversational AI assistant within Cursor, allowing users to ask questions, get explanations, and request code modifications using natural language. The Chat is context-aware, meaning it considers the current file and other provided context.
*   **Codebase Indexing:** The process of analyzing and creating a searchable index of a project's codebase. This index enables Cursor to quickly find relevant code snippets when answering questions or generating code.
*   **Composer:** Cursor's AI-powered code generation and editing tool. It allows users to provide instructions for multi-file edits or new code creation, and then review and apply the AI's proposed changes.
*   **Context:** The information provided to the AI model along with a prompt. This can include code snippets, entire files, documentation, web search results, or custom rules.  Providing sufficient context is crucial for accurate and relevant AI responses.
*   **Cursor AI:** An AI-powered code editor built upon a foundation similar to Visual Studio Code. It integrates large language models to assist with code completion, generation, explanation, and refactoring.
* **Cursor Rules:**  Customizable instructions that guide the AI's behavior and style.  Rules can be global (applying to all projects) or project-specific.
*   **Global Rules:**  AI rules that apply to all projects within a Cursor installation. These are set in Cursor's settings.
*   **Model Context Protocol (MCP):** An open protocol allowing Cursor's Agent to interact with external tools and services.
*   **Multi-Model Consensus:** A feature (potentially available in Pro/Enterprise versions) where Cursor uses multiple AI models to generate and verify solutions, improving accuracy and reliability.
* **Partial Accept:** Within a multi-line autocomplete suggestion, partially accept by word using keyboard command.
*   **Privacy Mode:** A setting in Cursor that, when enabled, ensures that code is not stored on Cursor's servers after processing, enhancing data privacy.
*   **Project-Specific Rules:** AI rules that apply only to a specific project. These are stored in the `.cursor/rules/` directory within the project.
*   **Prompt:** The instruction or question given to the AI in Chat, Composer, or the inline prompt bar.
* **Prompt Bar (Inline Prompt):**  Quick-access to prompt the AI in the current file, initiated with keyboard command, to accomplish tasks
* **Rules for AI**: A system for customizing and giving instruction to the AI to establish and enforce code standards, preferences, and project specific guidelines
* **YOLO Mode:**  A mode of the Agent, that when set, tells the Agent to take actions (like terminal commands) without user confirmation.
*   **@ Symbols:** Special prefixes used in Chat and Composer prompts to inject specific context, such as `@File`, `@Folder`, `@Codebase`, `@Docs`, and `@Web`.

## Keyboard Shortcut Reference

Here's a categorized list of keyboard shortcuts for Cursor on macOS.  (Note: For Windows/Linux, substitute `Ctrl` for `Cmd` in most cases).

**General:**

*   `Cmd + L`: Toggle/open Chat panel.
*   `Cmd + I`: Open a new Composer tab.
* `Cmd + N`: Create a new Composer thread/tab (When in Composer)
*   `Cmd + Shift + J`: Open Cursor Settings panel.
*   `Cmd + Shift + P`: Open Command Palette.
*   `Cmd + Alt + L`: Open Chat/Composer history view.

**Chat Specific:**

*   `Enter`: Send chat message (uses current file context).
*   `Cmd + Enter`: Send chat message with Codebase context (search entire project).
*   `↑ / ↓` (in input): Cycle through previous chat messages (edit last question).
*   `Cmd + L` (with text selected in editor): Add selection to a new chat prompt.
*   `Cmd + Shift + L` (with text selected): Add selection to the *current* chat context.

**Composer Specific:**

*   `Ctrl/Cmd + .`: Toggle Agent mode in Composer.
*   `Cmd + Enter`: Accept all changes in diff (apply all).
*   `Cmd + Backspace`: Cancel generation (stop) or reject all pending changes.
*   `Tab`: Move to next message field/iteration (or navigate agent steps).
*   `Shift + Tab`: Move to previous message/iteration.
*   `Cmd + [` or `Cmd + ]`: Navigate between Composer tabs (previous/next).
*   `Cmd + W`: Close Composer tab.

**Code/Editor:**

*   `Tab`: Accept inline suggestion.
*   `Esc`: Dismiss suggestion.
*   `Ctrl/Cmd + →`: Accept next *word* of suggestion (Partial Accept).
*   `@`: Open @-symbol menu for context (then navigate suggestions with arrows, `Enter` to select).
*   `Cmd + K`: Open inline prompt bar (for quick, single-file AI actions).
* `Cmd + Shift + K`: With text selected, add selection to Composer input context

**Terminal (Agent related):**

*   `Cmd + K`: Open Terminal prompt bar (for AI to suggest commands).
*   `Cmd + Enter`: Execute the suggested command in terminal prompt bar.
*   `Esc`: Dismiss/close the terminal prompt or cancel an auto-suggested command.

## Configuration File Reference

*   **`.cursor/rules/` (Directory):**
    *   *Purpose:* Contains project-specific AI rules. Each rule is typically a separate markdown file (e.g., `python_style.md`, `frontend_rules.mdc`).
    *   *Location:*  Within the root directory of a project.
    *   *Syntax:*  Each rule file contains plain text instructions, optionally with:
        *   A `Description:` at the top explaining the rule's purpose.
        *   `Globs:` or `Patterns:` lines specifying file patterns (glob patterns) to which the rule applies (e.g., `Globs: **/*.py`).
        *   The actual rule instructions, often formatted as bullet points or numbered lists.  These are natural language instructions for the AI.
    *   *Example:*
        ```markdown
        Description: Python coding style guidelines
        Globs: **/*.py

        - Use 4 spaces for indentation.
        - Include type hints in function definitions.
        - Prefer list comprehensions over explicit loops when appropriate.
        ```

*   **`.cursorignore` (File):**
    *   *Purpose:* Specifies files and directories to exclude from Cursor's codebase indexing.  This improves performance and prevents irrelevant files from being included in the AI's context.
    *   *Location:* Within the root directory of a project.
    *   *Syntax:*  Identical to `.gitignore` syntax. Each line contains a glob pattern.  `#` denotes comments.
    *   *Example:*
        ```
        # Ignore build output
        /dist/
        *.log

        # Ignore large data files
        data/*.csv

        # Ignore environment-specific secrets
        .env
        ```

* **`settings.json` (File):**
    * *Purpose:* While standard VS Code has many settings, Cursor introduces some of it's own.
    * *Location:* MacOS:  `~/Library/Application Support/Cursor/User/settings.json`

## References
1.  [Cursor AI: A Guide With 10 Practical Examples | DataCamp](https://www.datacamp.com/tutorial/cursor-ai-code-editor)
2.  [Cursor for Developers: Ultimate Introduction](https://www.builder.io/blog/cursor-ai-for-developers)
3.  [Features | Cursor - The AI Code Editor](https://www.cursor.com/features)
4.  [Cursor – Agent](https://docs.cursor.com/agent)
5.  [Security | Cursor - The AI Code Editor](https://www.cursor.com/security)
6.  [Cursor – Overview](https://docs.cursor.com/context/@-symbols/overview)
7.  [Cursor – Rules for AI](https://docs.cursor.com/context/rules-for-ai)
8.   [Cursor – Codebase Indexing](https://docs.cursor.com/context/codebase-indexing)
9. [All Cursor Shortcuts Guide: Composer, AI Pane, and more. - Refined](https://refined.so/blog/cursor-shortcuts-guide)
10.  [Cursor – Installation](https://docs.cursor.com/get-started/installation)
11. [Cursor – Advanced Features](https://docs.cursor.com/tab/advanced-features)
12. [Are You Really Using the Prompt Bar (Cmd K) Feature Effectively?](https://cursor101.com/tutorial/learn-cursor-cmdk)
13.  [Cursor – Composer](https://docs.cursor.com/composer)
14. [Exploring Cursor: Accessing External Documentation using @Doc](https://www.rudrank.com/exploring-cursor-accessing-external-documentation-using-doc/)
15. [Exploring Cursor: Browsing the Web for Resources using @Web](https://www.rudrank.com/exploring-cursor-browsing-web-for-swiftui-documentation/)
16.  [Cursor – Common Issues](https://docs.cursor.com/troubleshooting/common-issues)
17. [Mastering Cursor Rules: A Developer's Guide to Smart AI Integration - DEV Community](https://dev.to/dpaluy/mastering-cursor-rules-a-developers-guide-to-smart-ai-integration-1k65)
18. [Overview - Cursor](https://docs.cursor.com/context/@-symbols/overview)
19. [Cursor – Troubleshooting Guide](https://docs.cursor.com/troubleshooting/troubleshooting-guide)
---

This Appendix provides a solid foundation for reference material. Remember to update the "References" section with the correct numbering as you finalize the citations in the main body of the guide.
