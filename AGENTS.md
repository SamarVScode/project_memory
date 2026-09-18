# 🤖 Agent Memory Bridge & Project Rules

## 🧠 Central Knowledge Base (Obsidian Vault)
* **Vault Path:** `C:\Users\User\project_memory\project_memory`
* **Projects Folder:** `C:\Users\User\project_memory\project_memory\Projects`
* **Services Folder:** `C:\Users\User\project_memory\project_memory\Services`
* **Rules Folder:** `C:\Users\User\project_memory\project_memory\Rules`
* **Dashboard Note:** `C:\Users\User\project_memory\project_memory\Dashboard.md`

## 📋 Memory Directives for AI Agents
1. **Context Retrieval:** At the beginning of tasks, inspect the project's corresponding blueprint in the Obsidian vault (`C:\Users\User\project_memory\project_memory\Projects\<project-name>.md`) for environment variables, runtime versions, entry points, and architectural rules.
2. **Living Documentation:** Whenever changes are made to dependencies, ports, API routes, or environment configs, sync those updates back into the Obsidian note so the knowledge base remains current.
3. **Architecture Consistency:** Strictly adhere to the design patterns and ADRs documented in the vault.
4. **Onboarding New Codebases:** When creating memory documentation for a newly added codebase or service, strictly follow `C:\Users\User\project_memory\project_memory\Rules\How-to-Add-New-Codebase-Memory.md`. Enforce all 19 sections, the two mandatory Section 1 subheadings (`### The Operational Problem` and `### The Architectural Solution`), monorepo isolation, and QA gates.
5. **Updating Existing Memory:** When modifying or maintaining an existing memory note, strictly follow `C:\Users\User\project_memory\project_memory\Rules\How-to-Update-Codebase-Memory.md`. Execute surgical, incremental patches rather than regenerating from scratch, preserve the original `created` date, update the Changelog (Section 16), and recalibrate line citations.
6. **GAS Web App Architecture Standard:** When designing, developing, refactoring, or reviewing Google Apps Script web applications or data pipelines, strictly consult `C:\Users\User\project_memory\project_memory\Rules\GAS-Architecture-Index.md`. Triage the task to its matching App Archetype (A through F), inspect ONLY the designated line ranges in `C:\Users\User\project_memory\project_memory\Rules\GAS-Webapp-Architecture-Rulebook.md` to conserve context, strictly enforce the Non-Negotiable Core Laws alongside the Enterprise TypeScript Standard (Native Clasp `.ts` with `module: "None"` and ambient contracts in `types.ts`), and pass all verification checks in Section 21 before finalizing code.
