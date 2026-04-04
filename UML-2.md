@startuml

abstract class DefenseHandler {
-next : DefenseHandler
+setNext(handler) : DefenseHandler
+handle(damage, target)
}

class DodgeHandler {
-dodgeChance : double
-random : Random
+handle(damage, target)
}

class BlockHandler {
-blockPercent : double
+handle(damage, target)
}

class ArmorHandler {
-armorValue : int
+handle(damage, target)
}

class HpHandler {
+handle(damage, target)
}

class ArenaFighter
class TournamentEngine

DefenseHandler <|-- DodgeHandler
DefenseHandler <|-- BlockHandler
DefenseHandler <|-- ArmorHandler
DefenseHandler <|-- HpHandler

DefenseHandler --> DefenseHandler : next
DodgeHandler --> ArenaFighter
BlockHandler --> ArenaFighter
ArmorHandler --> ArenaFighter
HpHandler --> ArenaFighter

TournamentEngine --> DefenseHandler : builds chain

@enduml