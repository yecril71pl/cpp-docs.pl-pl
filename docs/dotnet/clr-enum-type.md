---
title: Typ wyliczenia CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scope, of CLR enum
- enum struct keyword [C++]
- enum class keyword [C++]
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2416a306373db08c5e925b4987fc8a9273973c39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="clr-enum-type"></a>Typ wyliczenia CLR
Deklaracja i zachowanie wyliczenia zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Deklaracja typu wyliczeniowego rozszerzeń zarządzanych jest poprzedzony `__value` — słowo kluczowe. W tym miejscu będzie odróżnienia natywnym wyliczeniem wyliczenia CLR, która jest pochodną `System::ValueType`, podczas sugerowanie podobnych funkcji. Na przykład:  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 Nowej składni rozwiązuje problem odróżnienie macierzystego i wyliczenia CLR przez akcentowania rodzaj klasy drugie zamiast jego katalogów głównych typu wartości. W efekcie `__value` — słowo kluczowe jest odrzucany zastąpione para rozmieszczonych w odległości — słowo kluczowe `enum class`. Zapewnia to symetrycznego sparowanego — słowo kluczowe, w deklaracjach odwołania, wartości oraz klasy interfejsu:  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 W tłumaczeniu wartości wyliczenia pary `e1` i `e2` w nowej składni wygląda następująco:  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Oprócz małych zmiany składni zmieniono zachowanie typ wyliczenia CLR na kilka sposobów:  
  
-   Deklaracja przekazująca dalej wyliczenie CLR nie jest już obsługiwana. Nie istnieje żadne mapowanie. Po prostu oflagowane jako błąd kompilacji.  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   Rozpoznawanie przeciążenia między wbudowanych typów arytmetycznych i `Object` hierarchii klas została wycofana między wersji językowych dwóch! Jako efekt uboczny wyliczenia CLR są już niejawnie konwertowane typów arytmetycznych.  
  
-   W nowej składni wyliczenia CLR zachowuje własną zakresu, który nie jest w przypadku rozszerzeń zarządzanych. Wcześniej moduły wyliczające były widoczne w zakresie zawierającym wyliczenia. Teraz moduły wyliczające znajdują się w zakresie wyliczenia.  
  
## <a name="clr-enums-are-a-kind-of-object"></a>Obiekt rodzaju są wyliczenia CLR  
 Rozważmy następujący fragment kodu:  
  
```  
__value enum status { fail, pass };  
  
void f( Object* ){ Console::WriteLine("f(Object)\n"); }  
void f( int ){ Console::WriteLine("f(int)\n"); }  
  
int main()  
{  
   status rslt = fail;  
  
   f( rslt ); // which f is invoked?  
}  
```  
  
 Dla natywnych programisty C++, fizyczna odpowiedź na pytanie, których wystąpienia przeciążonego `f()` jest wywoływany jest `f(int)`. Wyliczenie jest symboliczne stałej całkowitej i uczestniczy w standardowe integralną promocji, które mają pierwszeństwo w takim przypadku.  Ale w rzeczywistości w zarządzanych rozszerzeń to wystąpienie, do którego rozpoznaje wywołania. To spowodowane liczba niespodzianki — nie użyliśmy ich natywnych języka C++ ramki of pamiętać — ale czego potrzeba do interakcji z istniejących framework BCL (Biblioteka klasy podstawowej), gdzie `Enum` klasy pośrednio pochodzi z `Object`. W projekcie języka Visual C++, wystąpienie `f()` wywoływane jest `f(Object^)`.  
  
 Visual C++ włączył wyegzekwować to w sposób jest obsługuje niejawnej konwersji między typem wyliczenia CLR i typów arytmetycznych. Oznacza to, wszystkie przypisania obiektu typu wyliczenia CLR na typ arytmetyczny wymaga jawnego rzutowania. Przykładowo, podana tak,  
  
```  
void f( int );  
```  
  
 jako metodę nieprzeciążonymi w zarządzanych rozszerzeń wywołania  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 jest ok i wartości zawartych w `rslt` jest niejawnie konwertowane na wartość całkowitą. W programie Visual C++ to wywołanie nie powiodło się skompilować. Aby poprawnie przekształca ją, możemy Wstaw operatora konwersji:  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## <a name="the-scope-of-the-clr-enum-type"></a>Zakres typ wyliczenia CLR  
 Jeden z zmiany między języków C i C++ jest dodanie zakresu w obrębie obiektu struktury w języku C++. W języku C struktury jest tylko dane agregacji bez obsługi interfejsu lub skojarzonego zakresu. To dość radykalne usprawnienie zmiany w czasie, a czasami jest sporne problemem w przypadku wielu użytkowników C++ nowe pochodzące z języka C. Relacja między natywne i wyliczenia CLR jest analogiczna.  
  
 W zarządzanych rozszerzeń została podjęta próba zdefiniowania lekko wprowadzony nazwy moduły wyliczające wyliczenia CLR w celu symulowania braku zakresie w natywnym wyliczeniem. Udowodnić to nie powiodło się. Problem dotyczy, powoduje to moduły wyliczające do zostaną przeniesione do globalnej przestrzeni nazw, co powoduje trudno było zarządzać konflikty nazw. W nowej składni firma Microsoft ma były zgodne innych języków CLR obsługi zakresów w ramach wyliczenia CLR.  
  
 Oznacza to, że niekwalifikowane użycia modułu wyliczającego wyliczenia CLR nie zostaną rozpoznane przez nowej składni. Oto przykład rzeczywistych.  
  
```  
// Managed Extensions supporting weak injection  
__gc class XDCMake {  
public:  
   __value enum _recognizerEnum {   
      UNDEFINED,  
      OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6,  
   };  
  
   ListDictionary* optionList;  
   ListDictionary* itagList;  
  
   XDCMake() {  
      optionList = new ListDictionary;  
  
      // here are the problems...  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 Używa każdego z trzech niekwalifikowanych nazw modułu wyliczającego (`(1)`, `(2)`, i `(3)`) musi być kwalifikowana w tłumaczeniu do nowej składni, aby skompilować kod źródłowy. Oto poprawne tłumaczenie oryginalnego kodu źródłowego:  
  
```  
ref class XDCMake {  
public:  
   enum class _recognizerEnum {  
      UNDEFINED, OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6  
   };  
  
   ListDictionary^ optionList;  
   ListDictionary^ itagList;  
  
   XDCMake() {  
      optionList = gcnew ListDictionary;  
      optionList->Add("?",_recognizerEnum::OPTION_USAGE); // (1)  
      optionList->Add("help",_recognizerEnum::OPTION_USAGE); //(2)  
      itagList = gcnew ListDictionary;  
      itagList->Add( "returns",   
         _recognizerEnum::XDC0004_WRN_XML_LOAD_FAILURE); //(3)  
   }  
};  
```  
  
 Spowoduje to zmianę strategii projektowania między natywny i wyliczenia CLR. Wyliczenia CLR, obsługa skojarzonego zakresu w programie Visual C++ go nie jest konieczne ani skuteczne hermetyzacji w deklaracji wyliczenia w klasę. Ta idiom ewoluował w czasie zbliżonym cfront 2.0 w laboratoriach dzwonka również w celu rozwiązania problemu zanieczyszczenie globalną nazwę.  
  
 Oryginalne wydanie beta nowej biblioteki iostream przez Jerry Schwarz w laboratoriach dzwonka, Jerry nie Hermetyzowanie wszystkich wyliczeniach skojarzone zdefiniowane dla biblioteki i wyliczenia wspólne, takie jak `read`, `write`, `append`i tak dalej , uniemożliwił niemal dla użytkowników skompilować ich istniejącego kodu. Jedno rozwiązanie byłoby mangle nazwy, takie jak `io_read`, `io_write`itp. Drugim rozwiązaniem byłoby Aby zmodyfikować język przez dodanie zakresu do wyliczenia, ale nie było to możliwe w czasie. Środkowy rozwiązanie było Hermetyzowanie wyliczenia w ramach klasy lub klas hierarchii, gdzie nazwę tagu i moduły wyliczające wyliczenia wypełnić otaczającym zakresie klasy.) Oznacza to, że powód umieszczenia wyliczenia w klasach co najmniej pierwotnie nie filozoficzne, ale praktyczne odpowiedzi problemu globalne zanieczyszczenie przestrzeni nazw.  
  
 Wyliczenia Visual C++ nie ma żadnych istotnych korzyści hermetyzując wyliczenia w klasę. W rzeczywistości, jeśli przyjrzymy się `System` przestrzeni nazw, zobaczysz tego wyliczenia, klasy i interfejsy której z tą samą przestrzenią deklaracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wartości i ich zachowania (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Enum — klasa](../windows/enum-class-cpp-component-extensions.md)