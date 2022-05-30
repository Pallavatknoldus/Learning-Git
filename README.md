# Learning-Git

<details><summary><strong>CatchAll</strong><p>Handling exception using catchAll ...</p></summary>

```scala
object HandlingExceptionUsingCatchAll extends zio.App {

  val zFailed: IO[String, Nothing] = ZIO.fail("Some failure")

  val zCatchAll: ZIO[Any, Nothing, String] = zFailed.catchAll { _ =>
    ZIO.succeed("I will catch you from fail.")
  }

  override def run(args: List[String]): URIO[zio.ZEnv, ExitCode] = {
    (for {
      value <- zCatchAll
      _ <- zio.console.putStrLn(value)
    } yield ()).exitCode
  }
}
```
</details>


## Prerequisites

| S No. | Tools | versions |
|--|--|--|
| 1. | Scala | v2.13 |
| 2. | SBT | v1.4.3 |
