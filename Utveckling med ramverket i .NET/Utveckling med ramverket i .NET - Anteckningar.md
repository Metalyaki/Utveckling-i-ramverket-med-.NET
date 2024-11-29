## README
Filen blir din egen kopia, inget delas med någon annan. 

Börja med att gå in i Options>Editor>Behavior och stäng av Spellcheck.

Gå in i Appearance>Theme>Manage och välj ett annat tema, jag kör på "Obsidian Gruvbox", du kan även välja dark mode inne i "Theme".

För att skapa ett kodblock:
https://gyazo.com/d030707684b6370f80fbeb7ba640ad2f

För att göra ett radbryt skriver du 3st bindestreck: ---

---
Här kan du se mer formatteringstips i Obsidian
https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax

---
## Innehåll
- [[#V.48]]
- [[#V.49]]
- [[#V.50]]
- [[#V.51]]
- [[#V.52]]
- [[#V.01]]
- [[#V.02]]
- [[#V.03]]
- [[#V.04]]
## Övergripande anteckningar
---
Köp [Bok](https://www.amazon.se/-/en/Mark-J-Price/dp/183588122X?dib=eyJ2IjoiMSJ9.bBrDUPsdjKwLPW7tp46kxcAUNm7TYBt04CJduX_jF2k-IOX8OFMrm7xdURsuN4pPiSfG1iu1_AvKksQiOis35qIvf7EtoSfr638o7nCBMl9o8SkmIZ7wwgBFvNApzeMQy9ZGrEZTTa_HAeLlKS4w-kn6fvr9_B60Yhr1d5_CtZPV8VEcMgoBhzqHFk5X9_5KWxrJEJFkBZijbCGq7ZI-rHDEOAnQAvErcowxokFUpoU.g3VdGUXGxXX-aPjyVPbdshZw8mwRyMHFSFaxGylPIhc&dib_tag=se&qid=1732527398&refinements=p_27%3AMark+J.+Price&s=books&sr=1-15)

---
Quiz varje fredag

---
Använd tilldelade PDF av lärare.
Visual Studio Installer för att ändra i Visual Studio och Visual Studio Code.

---
Testa olikhet för att hitta likhet, sök olikhet.

---
## Terminologi
---
**Encapsulation**
Gör allting private som du inte behöver ha som public. Skriv inget och de sätts till private automatiskt.

**Inheritance**
Endast ärvande klasser kan använda propertys och metoder som är protected.

**Polymorfism**
Använd barnet om barnet finns
Virtual och override - Talar om att polymorfism skall användas om barnet finns.
Föräldern kan uppträda som barnet, när det behövs.

- String interpolation = **$**"Hej {Namn}"
- Expression bodied member: **=>**
- **As** "Funkar det så funkar det, annars blir det null." As är en softcast.
- 


 pascalCase
 CamelCase

---
## Externa länkar
***

https://docs.microsoft.com/en-us/dotnet/csharp/
https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/
https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/
https://docs.microsoft.com/en-us/dotnet/
https://learn.microsoft.com/en-us/dotnet/api/?view=net-8.0
https://stackoverflow.com/
https://www.geeksforgeeks.org/

---
## V.48 
### 25/11 Måndag
***
**IEquatable** interface för att ändra **Equals()** så att den jämför definierade värden istället för referenser. 
**IComparable** jämför två objekt, om dom är lika. Används för att jämföra likheter.

---
Om man har **init;** kan man sätta värden till propertys i {} efter en konstruktor.
Exempel:
```cs
	 Person person = new person() {FirstName = "Alfons", LastName = "Newberg", BirthDay = new DateTime(1997,08,01)};
```

*** 
För att formatera en DateTime till att endast visa år/månad/dag så skriver man "BirthDay:D"
Exempel: 
```cs
	Console.WriteLine($"Han är född {BirthDay:D}");
```

---
**ToString()** är polymorfiskt, används för att definera vad som skall skrivas ut i class, interface, record, struct. 
Gör **ToString()** för att få rätt textrepresentation.

***
Lägg alla **Console.WriteLine()** i Main, inte i modellen. 
Modell är ett samlingsord för vad du vill skapa, oavsett om det är en klass, struct eller record.

---
### 26/11 Tisdag
---
Alla värdetyper hamnar på stacken.
Alla referenstyper hamnar på heapen med referens på stacken.

---
Statiska propertys hamnar i en och samma instans som gäller för alla skapade instanser.
Dessa skapas när programmet startas med något som heter "Runtime".
Exempel:
```cs
Public Static Int NrInstances;
```

---
Field är en vanlig variabel fast i en klass, som kan vara "readonly", "public", "private " "protected"
Expression bodied member: **=>**

**Backing field**
Göra någonting när du sätter ett värde till en property.
Exempel:
``` cs
	private int _age;
	public int Age { get { return _age; }
		set
		{
			if (value <= 0 || value > 100)
				throw new  ArgumentException("Wrong Age");

            _age = value;
		}
	}
```

---
**Argument och Parameter**
Varje argument anropar en parameter. Använder parametrar vid deklaration.
Metoder använder parametrar och läser in argument.

Parametrar skall vara pascalCase

```cs
       static int AddTwoNumbers (int a, int b) // Parameter
    {
        var c = a + b;
        return c;
    }
    var result = AddTwoNumbers(6, 7); // Argument


	   static void Greetings (string name) // Parameter
    {
        Console.WriteLine($"Hello {name}");
    }
    Greetings("Alfons"); // Argument
```

---
**Copy constructor**
Måste kopiera en redan instansierad instans för att kunna kopiera värden till copy constructorn.

```cs
        public Car(Car original) // Car 2 propertys
        {
            Color = original.Color;
            Brand = original.Brand;
            Model = original.Model;
        }

		var car2copy = new car(car2) // Kopierar property-värden från car2
```

Kan fortfarande sätta egna värden på propertys i objekt initieringen.
Exempel
```cs
var car2copy = new car(car2) { Color = CarColor.Burgundy};
```

---
**Referens copy**
Ute efter hastighet
Både lista och objekt är samma som orginalet. 

Inget unikt, allting samma.

**Shallow copy**
En shallow copy kopierar listan eller arrayen, skapar ett nytt objekt men behåller samma referens som orginalet. 

Unik lista, samma objekt.

**Deep copy**
Använd copy construktor för att göra en deep copy.
Varje gång en instans skapas så skapas en ny kopia.
Tar mycket tid för allt ska kopieras.

Unik lista, unika objekt.

---
### 27/11 Onsdag

---
Finns 3 sätt att sätta värden, Get/Set, Objektinitiering, propertys.

**ToString()**, så objektet kan representera sig själv i text.

I Private Backing Field är standard att namnge fields med _
Exempel:
```cs
        private decimal _price; //Private backing field
        public decimal Price //Property
        { //Designmetodologi/Mönstret
            get => _price;
            set
            {
                if (value <= 0)
                {
                    throw new Exception("Price cannot be 0 or negative");
                }
                else
                {
                    _price = value;
                }
            }
        }
```

---
**Text konstanter**
**F** - Float 
**D** - Double 
**M** - Money 
Sök på "String interpolation formatting" för att hitta fler

**Cx** = Currency
**Nx** = Number
x = Antal decimaler

Decimal är Microsofts rekommendation att använda när man jobbar med pengar, för att den är precis.

---
**Statisk polymorfism & Overload** 
Statisk polymorfism är metoder med samma namn och returvärde men olika parametrar. Sådana metoder kallas "**Overload methods**".
```cs
    public string AddLastName(string LastName)
    {
        Name = Name + " " + LastName;
        return Name;
    }

	//Overload metod
    public string AddLastName(string LastName, string MiddleName)
    {
        Name = Name + " " + MiddleName + " " + LastName;
        return Name;
    }
```

---
**This** 
Används för att förebygga namnkonflikter. Kan användas för att urskilja från **base**.
```cs
    public Student(string Name, int Grade = 5)
    {
        this.Name = Name;
        this.Grade = Grade;
    }
```

Kan användas för att köra flera konstruktorer.
```cs
		//På grund av this på rad 9 så körs sedan denna konstruktor.
        public Stock(string _name, decimal _price, int _amount)
        {
            Name = _name;
            Price = _price;
            Amount = _amount;
        }
	    //Först körs denna konstruktor.
        public Stock(string _name, decimal _price) : this(_name, _price, 0)
        {
            Name = _name;
            Price = _price;
            Amount = 0;
        }
```
---
**Operator Overloading**
Ändra definition på operatorer.
`==, <=, >, !=, x++,x--`

Används främst till `== & !=`.

```cs
 public static bool operator == (WineAsClass w1, WineAsClass w2)
 {
     bool res = 
         (w1.Name, w1.Country, w1.GrapeType, w1.WineType) ==
         (w2.Name, w2.Country, w2.GrapeType, w2.WineType);
     return res;
 }
//Annan struktur där => ersätter { } och return.
 public static bool operator !=(WineAsClass w1, WineAsClass w2) =>
 (w1.Name, w1.Country, w1.GrapeType, w1.WineType) !=
 (w2.Name, w2.Country, w2.GrapeType, w2.WineType);
```

---
**IEquatable<> & Equals()**
Interfacet **IEquatable<>** tvingar dig att använda Equals().
Går att göra en override på Equals() metoden för att definera jämföringen.

När du behöver gå från referenslikhet till värdelikhet behöver man göra 3 saker.
1. IEquatable & Equals()
2. Operator overload om du behöver definera operatorer
3. Implementera GetHashCode för att motverka legacyproblem

```cs
//Definera vilka parametrar som skall jämföras mot varandra.
//Första kravet för IEquatable, räcker för att programmet skall vara nöjd.
        public bool Equals(Wine other) => 
            (this.Name, this.GrapeType, this.WineType, this.Country, this.Price) ==
            (other.Name, other.GrapeType, other.WineType, other.Country, other.Price);

//Override på Equals() metoden för att definera object till Wine.
//Andra kravet för IEquatable, gör detta för att förhindra fel vid användning av object. Man gör en "cast" på object.
        public override bool Equals(object obj) => Equals(obj as Wine);
       
//Definera vad GetHashCode() skall använda för att sätta hashkod.
//Tredje kravet för IEquatable. Säkerställer att objekt som är lika enligt Equals har samma hashkod. Vissa algoritmer använder hashcode.
        public override int GetHashCode() => (this.Name, this.GrapeType, this.WineType, this.Country, this.Price).GetHashCode();
```

**Operator overload med Equals()**
```cs
//Om man inte definerar Equals() med en override skriver man på detta vis för att göra en operator overload.
        public static bool operator ==(Wine One, Wine Two) =>
            (One.Name, One.GrapeType, One.WineType, One.Country, One.Price) ==
            (Two.Name, Two.GrapeType, Two.WineType, Two.Country, Two.Price);
            
        public static bool operator !=(Wine One, Wine Two) =>
            (One.Name, One.GrapeType, One.WineType, One.Country, One.Price) ==
            (Two.Name, Two.GrapeType, Two.WineType, Two.Country, Two.Price);

//Om definerad override på Equals() finns, då kan man skriva såhär.
	public static bool operator ==(Wine One, Wine Two) => One.Equals(Two);
    public static bool operator !=(Wine One, Wine Two) => !One.Equals(Two);
```

**GetHashCode**
Är en integer, del av object klassen.
.NET tittar på instansen och genererar ett tal. 
GetHashCode() garanterar att två stycken instanser som är lika har samma tal.

```cs
        int i = 3;
        Console.WriteLine(3.GetHashCode()); //3
        Console.WriteLine(i.GetHashCode()); //3

        string s = "Hello";
        Console.WriteLine("Hello".GetHashCode()); //-1355785695
        Console.WriteLine("HelLo".GetHashCode()); //722723394
        Console.WriteLine(s.GetHashCode()); //-1355785695

        var cs_w1 = new WineAsClass("Nice evening", Country.Spain,
            GrapeType.Tempranillo, WineType.Red, 80M);
        Console.WriteLine(cs_w1.GetHashCode()); //43942917

		//cs_w1 och cs_w2 har samma argument men ändå olika HashCodes

        var cs_w2 = new WineAsClass("Nice evening", Country.Spain,
            GrapeType.Tempranillo, WineType.Red, 80M);
        Console.WriteLine(cs_w2.GetHashCode()); //59941933

		//Override på GetHashCode() gör en tuple på det som ska bli en HashCode.
	    public override int GetHashCode() => (Name, Country, GrapeType, WineType).GetHashCode();

        var cs_w1 = new WineAsClass("Nice evening", Country.Spain,
            GrapeType.Tempranillo, WineType.Red, 80M);
        Console.WriteLine(cs_w1.GetHashCode()); //-684831212

		//Med override så får man samma HashCode.

        var cs_w2 = new WineAsClass("Nice evening", Country.Spain,
            GrapeType.Tempranillo, WineType.Red, 80M);
        Console.WriteLine(cs_w2.GetHashCode()); //-684831212

```

---
**Jämföra två listor**
```cs
//Sök olikheter i listorna för att se ifall de är lika.
        public bool Equals(WineCellar other)
        {
            if (other == null) return false;
            if (other.Name != Name) return false;
            if (other.Wines.Count != Wines.Count) return false;

            for (int i = 0; i < Wines.Count; i++)
            {
                if (other.Wines[i] != Wines[i]) return false;
            }

            return true;
        }

```
---
**Object**
Alla klasser ärver av object.

---
**Polymorfism exempel**
Polymorfism är ett samspel, måste bestämmas innan basklass skapas om ärvande klasser ska kunna nyttja polymorfism.

Viktigt att tänka på vart tittar ditt objekt, mot föräldern eller barnet.

Sätt new i propertys om du vill säkerställa att du definerar propertys från barnet. public new int Age = 17;

```cs

//När animal skapas så skapas instans av Animal.
Animal a = new Animal();
Console.WriteLine($"{a.Name} says {a.Noise()}. I am {a.Age} years old."); 
//"Max the animal says Clonk. I am 0 years old."

/*
När dog skapas så skapas instans av både animal och Dog. Den går in i Dog klassen för att definera Namn, Noise och Age.
Eftersom barnet ärver av föräldern. Så kommer namnet på Dog instansen sättas till namnet från Name propertyn i Animal. OM man inte sätter ett Name i Dog klassen.
 */
Dog d = new Dog();
Console.WriteLine($"{d.Name} says {d.Noise()}. I am {d.Age} years old."); //"Cooper the Dog says Voff. I am 17 years old."

Animal d1 = d; //Den blir av typen Dog men hittar endast propertys från Animal. Den blir en Dog men ser endast Animal, sin basklass.

//Med virtual och override så kan d1 få propertys och metoder från Dog.
Console.WriteLine($"{d1.Name} says {d1.Noise()}. I am {d1.Age} years old."); //"Max the animal says Clonk. I am 0 years old."

Cat c = new Cat();
Console.WriteLine($"{c.Name} says {c.Noise()}. I am {c.Age} years old.");

Animal c1 = c; //Den blir av typen Cat men hittar endast propertys från Animal.
Console.WriteLine($"{c1.Name} says {c1.Noise()}. I am {c1.Age} years old.");
Console.WriteLine();

//Kan ej innehålla ärvande klasser, endast av klassen Dog
var animals = new List<Dog>();

//Kan innehålla alla ärvande klasser, Cat och Dog
var animals1 = new List<Animal>();

animals1.Add(a);
animals1.Add(d);
animals1.Add(d1);
animals1.Add(c);
animals1.Add(c1);

foreach (var item in animals1)
{
    Console.WriteLine($"{item.Name} says {item.Noise()}. I am {item.Age} years old.");
    if (item is Dog dog)
    {
        Console.WriteLine(dog.Hate()); 
        //Föräldern har inget med Hate() att göra, endast Dog har tillgång till den.
    }

}

```

---
**Virtual & Override**
Vanligt att sätta propertys i basklassen till virtual så du kan komma åt barnet.
Fields kan ej vara virtual eller override.
```cs
	public class Chef
{
    public virtual string Name => "Boring";
    public virtual string Hello => $"Hello";
    public virtual string FavoriteDish => "nothing";
    public override string ToString() => $"{Hello}, I am {Name}. I like {FavoriteDish}. I am a {GetType()}";

}

public class FrenchChef : Chef
{
    public override string Name { get; }
    public override string Hello { get; }
    public override string FavoriteDish { get; }

    public FrenchChef(SeedGenerator rnd)
    {
        Name = rnd.FullName;
        Hello = "Bonjour";
        FavoriteDish = rnd.FromString("Escargot, Beuf Borgignon, Pizza");
    }
}
```


**Bildexempel på polymorfism**
[[Whiteboard]]

### 28/11 Torsdag
---

**Interface**
När man skall skapa ett interface så måste man avgöra vilka medlemmar i ärvande klasser som skall vara public. Interface kan inte innehålla private. Med hjälp av interface kan man jobba paralellt.

Använd interfacet som en typ så kan man implementera programmet även om det interfacet innehåller ej är klart. Klass, struct eller liknande.
Exempel:
```cs
IPearl p1 = null; // new Pearl();
``` 

Annat exempel:
```cs
INecklace necklace = null; //new Necklace();

IPearl p1 = null; //new PearlAsClass();
p1.Color = PearlColor.Black;
p1.Shape = PearlShape.DropShaped;
p1.Type = PearlType.SaltWater;
p1.Size = 5;

IPearl p2 = null; //new PearlAsStruct();
p2.Color = PearlColor.White;
p2.Shape = PearlShape.Round;
p2.Type = PearlType.FreshWater;
p2.Size = 25;

necklace.Name = "Sample Necklace";
necklace.ListOfPearls.Add(p1);
necklace.ListOfPearls.Add(p2);
```
Först när NeckLace, PearlAsClass och PearlAsStruct har implementerats så kan man addera detta till programmet. Innan det så sätter man dessa till null för att kunna skapa programmet, använda relevanta metoder och propertys till de klasser som skall skapas.

Skiljer implementation mot definition
Du kan inte instansiera men du kan kompilera.


**Seed()**
```cs
        public ICar Seed(SeedGenerator seeder)
        {
            Brand = seeder.FromEnum<CarBrand>();
            Model = seeder.FromEnum<CarModel>();
            RegNumber = $"{seeder.FromString("ABC, DET, ASD, GDF, WWE")}-{seeder.Next(100,1000)}";
            Year = seeder.Next(1970, 2024);
            Owner = new PersonAsClass().Seed(seeder);

            return this;
        }
```
Du kan använda dig av en metod för att ange värden till en klass. I detta fall är det även med hjälp av en SeedGeneratorklass. Där man sätter random värden till alla propertys.

**ToString()**
```cs
        public override string ToString() => 
            $"Hi, I am {Owner}. I drive a {Brand} {Model} from the year {Year}. " +
            $"My reg number is {RegNumber}, my email is {Owner.Email} and my type is {GetType().Name}.";
```
I detta exempel så innefattar **{Owner}** en egen klass med en egen **ToString()** metod som skrivs ut.
Man kan även skriva **{Owner.Email}** för att endast skriva ut propertys från klassen som är tilldelad till **{Owner}**.
Metoden **{GetType().Name}** skriver endast ut namnet på klassen som typen är av. Det finns andra definitioner att använda till **GetType()**-metoden.

```cs
//Denna skrivs ut när {Owner} anropas i metoden ovan.
        public override string ToString() => $"{FirstName} {LastName}";

```

**Record**
Immutable
Konstruktor och property i samma
Finns en ToString i record-format. Går att göra en override på denna
Det är som en klass, kan bygga vidare på record precis som en klass.

Enkel konstuktor med propertys i parantes
Lägg egna konstruktorer
Egna metoder
När ni ska ändra i en record så använder man With för att göra en kopia med ändrade värden. Man ändrar inte ursprunget

Skapa ny instans av record för att ändra ett värde.
```cs
var pearlRecord_Copy = pearlRecord with { Size = 5 };
```


### 29/11 Fredag - Föreläsning TEAMS

Ändra propertys till Init för att göra klassen immutable
Enklaste formen av immutable är record

Default sätter variabler till null eller 0.

**Pattern matching**
Switch expression
Sök specifikt i början
Is operator används i if-satser
Vanligaste sättet att använda switchexpression är i en metod

```cs
//Pattern matching using if - is
if (p1 is PearlAsClass)
{
    System.Console.WriteLine("Implemented as a class");
}
```

```cs
//Pattern matching using switch
var message = p1 switch
{
    PearlAsClass => "Implemented as a class",
    PearlAsStruct => "Implemented as a struct",
    PearlAsRecord => "Implemented as a record",
    
    _ => "discarded"
};
```

```cs
//Pattern matching in a method with switch using expression bodied member syntax
static string MethodPatternMatching(IPearl pearl) => pearl switch
{
    PearlAsClass => "Implemented as a class",
    PearlAsStruct => "Implemented as a struct",
    PearlAsRecord => "Implemented as a record",
    
    _ => "discarded"
};

System.Console.WriteLine(MethodPatternMatching(p1));
System.Console.WriteLine(MethodPatternMatching(p2));
System.Console.WriteLine(MethodPatternMatching(p3));
```

```cs
//Pattern matching in a method with switch using expression bodied member syntax
static string ComplexPatternMatching(IPearl pearl) => pearl switch
{
    //Order of most specific
    PearlAsRecord {Color: PearlColor.White } p when p.Size > 20 => "Large White Pearl, implemented as a Record ",

    PearlAsClass and IPearl {Color: PearlColor.White, Size: < 10}  => "Small White Pearl, implemented as a Class",

    IPearl p when p.Size < 10 && p.Color == PearlColor.Black => "Small Black Pearl, any implementation",

    PearlAsClass => "Implemented as a class",
    PearlAsStruct => "Implemented as a struct",
    PearlAsRecord => "Implemented as a record",
    
    _ => "discarded"
};

var pr = new PearlAsRecord(25, PearlColor.White, PearlShape.Round, PearlType.SaltWater);
System.Console.WriteLine(ComplexPatternMatching(pr));

var pr1 = pr with {Size = 5, Color = PearlColor.Black};
System.Console.WriteLine(ComplexPatternMatching(pr1));

var pc1 = new PearlAsClass(){ Color = PearlColor.White, Size = 7};
System.Console.WriteLine(ComplexPatternMatching(pc1));
```
## V.49
---
### 2/12 Måndag 

### 3/12 Tisdag

### 6/12 Fredag - Föreläsning TEAMS

## V.50
---
### 9/12 Måndag 

### 10/12 Tisdag

### 13/12 Fredag - Föreläsning TEAMS

## V.51
---
### 16/12 Måndag 

### 17/12 Tisdag

### 20/12 Fredag - Föreläsning TEAMS

## V.52
---
### 23/12 Måndag - Föreläsning TEAMS

### 27/12 Fredag - Föreläsning TEAMS

## V.01
---
### 3/1 Fredag - Föreläsning TEAMS

## V.02
---
### 7/1 Tisdag

### 10/1 Fredag - Föreläsning TEAMS

## V.03
---
### 15/1 Onsdag 

### 16/1 Torsdag

### 17/1 Fredag - Föreläsning TEAMS
## V.04
---
### 22/1 Onsdag 

### 23/1 Torsdag

### 24/1 Fredag - TENTA