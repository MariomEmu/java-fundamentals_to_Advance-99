# ⚡(Java Type Casting)


```
├── ১. প্রিমিটিভ টাইপ কাস্টিং (Primitive Casting)
│   ├── A. ইম্প্লিসিট (Widening)
│   │   ├─ byte → short, int, long, float, double
│   │   ├─ short → int, long, float, double
│   │   ├─ int → long, float, double
│   │   ├─ long → float, double
│   │   └─ float → double
│   └── B. এক্সপ্লিসিট (Narrowing)
│       ├─ double → float, long, int, short, byte, char
│       ├─ float → long, int, short, byte, char
│       ├─ long → int, short, byte, char
│       ├─ int → short, byte, char
│       ├─ short → byte, char
│       └─ char → byte, short
│
├── ২. অবজেক্ট টাইপ কাস্টিং (Object Casting - Inheritance)
│   ├── A. Upcasting (Child → Parent)
│   │   ├─ Dog → Animal
│   │   ├─ Cat → Animal
│   │   ├─ Puppy → Dog, Animal
│   │   └─ SmartDog → Animal, Dog, Pet, GuardAnimal
│   └── B. Downcasting (Parent → Child, instanceof needed)
│       ├─ Animal → Dog / Cat / Puppy / SmartDog
│       ├─ Dog → Puppy / SmartDog
│       └─ Pet / GuardAnimal → SmartDog
│
├── ৩. প্রিমিটিভ ↔ র‍্যাপার (Primitive ↔ Wrapper)
│   ├─ Auto Boxing (Primitive → Wrapper)
│   │   ├─ byte → Byte, short → Short, int → Integer
│   │   ├─ long → Long, float → Float, double → Double
│   │   └─ char → Character, boolean → Boolean
│   └─ Auto Unboxing (Wrapper → Primitive)
│       ├─ Byte → byte, Short → short, Integer → int
│       ├─ Long → long, Float → float, Double → double
│       └─ Character → char, Boolean → boolean
│
├── ৪. র‍্যাপার → র‍্যাপার কাস্টিং (Wrapper to Wrapper)
│   ├─ Unbox → Cast → Box (৩-Step Process)
│   ├─ Integer → Double: Integer → int → double → Double
│   ├─ Integer → Long / Float / Short / Byte (Data Loss হতে পারে)
│   ├─ Long → Integer / Short / Byte (Overflow / Data Loss)
│   ├─ Float → Integer / Long / Short / Byte (Precision/Data Loss)
│   └─ Character → Integer / Double / Long / Float (ASCII/Unicode)
│
├── ৫. স্ট্রিং কাস্টিং (String Casting)
│   ├─ String → Primitive
│   │   ├─ "123" → byte, short, int, long
│   │   ├─ "123.45" → float, double
│   │   ├─ "A" → char
│   │   └─ "true" → boolean
│   └─ Primitive → String
│       ├─ byte, short, int, long → "123"
│       ├─ float, double → "123.45"
│       ├─ char → "A"
│       └─ boolean → "true"
│
├── ৬. স্পেশাল কেস (Special Cases: char & boolean)
│   ├─ char Casting
│   │   ├─ char → int (ASCII/Unicode), long, float, double
│   │   ├─ int/byte/short → char (explicit)
│   │   └─ char '5' → int (digit)
│   └─ boolean Casting
│       ├─ boolean → Boolean (Boxing)
│       ├─ Boolean → boolean (Unboxing)
│       ├─ boolean → String (valueOf)
│       ├─ String → boolean (parseBoolean)
│       └─ ❌ boolean ↔ int/char/other Wrapper (Not possible)
│
├── ৭. অ্যারে কাস্টিং (Array Casting)
│   ├─ Object Array casting supported
│   └─ Primitive Array: manual conversion via loop required
│
├── ৮. জেনেরিক্স কাস্টিং (Generics Casting)
│   └─ Type safety required, unchecked casts may give warnings
│
└── গুরুত্বপূর্ণ নোট (Important Notes)
    ├─ Upcasting: implicit & safe
    ├─ Downcasting: explicit & instanceof check needed
    ├─ boolean cannot be cast to other primitive types
    ├─ char casts take ASCII/Unicode values
    ├─ Wrapper → Wrapper casting may cause data loss
    ├─ String → primitive: use parseXxx() methods
    ├─ primitive → String: use String.valueOf()
    ├─ ClassCastException may occur at runtime (downcasting)
    └─ instanceof operator can be used for runtime type checking
```
