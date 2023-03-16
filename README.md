# Reproduce the scenario

This repo intends to demonstrate that Garden deploys with --var option works as expected.

````bash
garden deploy --var installCRDs=true
````

Result of the above command:

````bash
➜  cli-env-vars git:(master) ✗ garden deploy --var installCRDs=true
Deploy 🚀

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🌍  Running in namespace default in environment local
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✔ providers                 → Getting status... → Cached
   ℹ Run with --force-refresh to force a refresh of provider statuses.
✔ graph                     → Resolving 1 modules... → Done
✔ kong                      → Building version v-a86a0e745b... → Done (took 0 sec)
✔ kong                      → Deploying version v-e41fcb9f43... → Done (took 5.6 sec)
   ℹ kong                      → Resources ready

Done! ✔️
````

## If you don't send the env var

````bash
➜  cli-env-vars git:(master) ✗ garden deploy
Deploy 🚀

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🌍  Running in namespace default in environment local
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✔ providers                 → Getting status... → Cached
   ℹ Run with --force-refresh to force a refresh of provider statuses.
  graph                     → Resolving 1 modules...
Failed resolving one or more modules:

kong: Invalid template string (${var.installCRDs}): Could not find key installCRDs under var.

See .garden/error.log for detailed error message
````

## Conclusion

The command `garden deploy --var KEY=VALUE` works as expected.
