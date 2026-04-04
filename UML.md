@startuml

interface ActionCommand {
+execute()
+undo()
+getDescription() : String
}

class AttackCommand {
-target : ArenaOpponent
-attackPower : int
-damageDealt : int
+execute()
+undo()
+getDescription()
}

class HealCommand {
-target : ArenaFighter
-healAmount : int
-actualHealApplied : int
+execute()
+undo()
+getDescription()
}

class DefendCommand {
-target : ArenaFighter
-dodgeBoost : double
+execute()
+undo()
+getDescription()
}

class ActionQueue {
-queue : List<ActionCommand>
+enqueue(cmd)
+undoLast()
+executeAll()
+getCommandDescriptions() : List<String>
}

class ArenaFighter
class ArenaOpponent

ActionCommand <|.. AttackCommand
ActionCommand <|.. HealCommand
ActionCommand <|.. DefendCommand

ActionQueue --> ActionCommand
AttackCommand --> ArenaOpponent
HealCommand --> ArenaFighter
DefendCommand --> ArenaFighter

@enduml