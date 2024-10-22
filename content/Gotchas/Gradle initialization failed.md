---
tags:
  - gotchas
---
### Error:
```
Error building Player: CommandWithNoStdoutInvokationFailure: Gradle initialization failed.

CommandWithNoStdoutInvokationFailure: Gradle initialization failed.  
UnityEditor.Android.Command.RunWithShellExecute (System.String command, System.String args, System.String workingdir, System.String errorMsg) (at <c4379596d7a6422890664bcfc2916b9b>:0)  
UnityEditor.Android.AndroidJavaTools.RunJavaWithShellExecute (System.String args, System.String workingdir, System.String error) (at <c4379596d7a6422890664bcfc2916b9b>:0)  
UnityEditor.Android.GradleWrapper.WarmupGradle (UnityEditor.Android.AndroidJavaTools javaTools, System.String workingDir, System.String baseCommand) (at <c4379596d7a6422890664bcfc2916b9b>:0)  
Rethrow as GradleInvokationException: Gradle initialization failed.  
UnityEditor.Android.GradleWrapper.WarmupGradle (UnityEditor.Android.AndroidJavaTools javaTools, System.String workingDir, System.String baseCommand) (at <c4379596d7a6422890664bcfc2916b9b>:0)  
UnityEditor.Android.PostProcessAndroidPlayer+<>c__DisplayClass5_0.<ExecuteWarmup>b__0 () (at <c4379596d7a6422890664bcfc2916b9b>:0)  
System.Threading.ThreadHelper.ThreadStart_Context (System.Object state) (at <4b234520e36749be9cf6b053d911690f>:0)  
System.Threading.ExecutionContext.RunInternal (System.Threading.ExecutionContext executionContext, System.Threading.ContextCallback callback, System.Object state, System.Boolean preserveSyncCtx) (at <4b234520e36749be9cf6b053d911690f>:0)  
System.Threading.ExecutionContext.Run (System.Threading.ExecutionContext executionContext, System.Threading.ContextCallback callback, System.Object state, System.Boolean preserveSyncCtx) (at <4b234520e36749be9cf6b053d911690f>:0)  
System.Threading.ExecutionContext.Run (System.Threading.ExecutionContext executionContext, System.Threading.ContextCallback callback, System.Object state) (at <4b234520e36749be9cf6b053d911690f>:0)  
System.Threading.ThreadHelper.ThreadStart () (at <4b234520e36749be9cf6b053d911690f>:0)  
UnityEngine.<>c:<RegisterUECatcher>b__0_0(Object, UnhandledExceptionEventArgs)

```
### Solution:
Run unity hub as administrator.
### Documentation:

### Software:
[[Unity]] [[Augmented Reality]]
### Hardware:
[[Android Device]]

### Sources:
[^1]: https://discussions.unity.com/t/no-internal-option-on-android-build/724084/12
[^2]: https://stackoverflow.com/questions/56587710/i-am-not-able-to-build-android-app-in-unity3d-error-gradle-initialization-faile
