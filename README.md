# clj-commons-exec

[Apache Commons Exec](http://commons.apache.org/exec/) wrapper for Clojure

## Usage

    (require [clj-common-exec :as exec])

    (exec/sh "echo" "hello")   ; A promise is returned immediately.
    ;=> #<core$promise$reify__5727@12fa6824: :pending>

    @(exec/sh "echo" "hello")  ; To get a result, deref it.
    ;=> {:exit 0, :out "hello\n", :err nil}

    (exec/sh "ls" "-l" {:dir "/"}) ; Last argument can be recognized as an option map.

option
*:dir* **(String or java.io.File)** override the process dir.
*:in* **(String or InputStream)** is fed to the sub-process's stdin.
*:out* **(OutputStream)** is used as the sub-process's stdout.
*:err* **(OutputStream)** is used as the sub-process's stderror.
*:watchdog* **(int)** set watchdog timer in ms.
*:env* **(Map)** The environment for the new process. If null, the environment of the current process is used.
*:add-env* **(Map)** The added environment for the new process.
*:as-success* **(int)** is regarded as sucess exit value.
*:as-successes* **(sequence)** are regarded as sucess exit value.
*:result-handler-fn* **(function)** A function, which will be called with promiss, in, out, err and option map, create an instance of org.apache.commons.exec.ExecuteResultHandler. You should close in, out, and err stream manually.

## Installation
Leiningen [org.clojars.hozumi/clj-commons-exec "1.0.0-SNAPSHOT"]

## License

Copyright (C) 2011 FIXME

Distributed under the Eclipse Public License, the same as Clojure.