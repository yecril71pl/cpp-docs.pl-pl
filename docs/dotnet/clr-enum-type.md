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
ms.openlocfilehash: a39c451bcff7b5b3b1d7dd9f0d3925616b9d6aab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436230"
---
# <a name="clr-enum-type"></a>Typ wyliczenia CLR

Deklaracja i zachowaniem typów wyliczeniowych został zmieniony z zarządzanych rozszerzeń języka C++ do Visual C++.

Deklaracji enum zarządzanych rozszerzeń jest poprzedzony `__value` — słowo kluczowe. Tutaj będzie odróżnić natywnym wyliczeniem od wyliczenia CLR, który jest tworzony na podstawie `System::ValueType`, podczas sugerując funkcje analogiczne. Na przykład:

```
__value enum e1 { fail, pass };
public __value enum e2 : unsigned short  {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Nowej składni rozwiązuje problem odróżnianie natywnych i typów wyliczeniowych CLR, podkreślając charakter klasy one, a nie jego korzenie typu wartości. W efekcie `__value` — słowo kluczowe jest odrzucana zastąpione pary rozmieszczonych — słowo kluczowe `enum class`. Dzięki temu symetrii sparowane — słowo kluczowe, deklaracje odwołania, wartości i klas interfejsów:

```
enum class ec;
value class vc;
ref class rc;
interface class ic;
```

Tłumaczenie pary wyliczenie `e1` i `e2` w nowej składni wygląda następująco:

```
enum class e1 { fail, pass };
public enum class e2 : unsigned short {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Oprócz małych zmiany składniowe zachowanie typ wyliczenia CLR został zmieniony na kilka sposobów:

- Deklaracja wyliczenia CLR nie jest już obsługiwana. Nie istnieje żadne mapowanie. Po prostu oflagowane jako błąd w czasie kompilacji.

```
__value enum status; // Managed Extensions: ok
enum class status;   // new syntax: error
```

- Rozpoznanie przeciążenia między wbudowanych typów arytmetycznych i `Object` hierarchii klas została wycofana między wersjami języka dwóch! Jako efekt uboczny typów wyliczeniowych CLR nie jest już niejawnie są konwertowane do typów arytmetycznych.

- W nowej składni wyliczenia CLR przechowuje własny zakres, który nie jest w przypadku zarządzanych rozszerzeń. Wcześniej wyliczających były widoczne w zakresie zawierających wyliczenia. Teraz moduły wyliczające są hermetyzowane w zakresie wyliczenia.

## <a name="clr-enums-are-a-kind-of-object"></a>Typów wyliczeniowych CLR są obiektu rodzaju

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

Dla natywnych programistą języka C++ fizyczna odpowiedzi na pytanie, które wystąpienie przeciążonej `f()` jest wywoływany jest `f(int)`. Wyliczenie jest symboliczne stałą całkowitoliczbową i uczestniczy w standardowych awansowaniu całkowitoliczbowym, które mają pierwszeństwo w tym przypadku.  Ale w rzeczywistości w zarządzanych rozszerzeń to wystąpienie, do którego rozpoznaje wywołania. Przyczyną szereg niespodzianek — nie w przypadku, gdy użyliśmy ich pamiętać natywnego języka C++ ramki of — ale Musieliśmy je do interakcji z istniejącej struktury BCL (Biblioteka klasy podstawowej), gdzie `Enum` klasy pośrednio pochodzi od `Object`. W projekcie języka Visual C++, wystąpienie `f()` wywoływany jest `f(Object^)`.

Sposób, w jaki Visual C++ wybrał do wymuszania tej reguły jest, aby nie obsługiwać niejawnych konwersjach między typ wyliczenia CLR i typów arytmetycznych. Oznacza to, że wszelkie przypisanie obiektu CLR typu wyliczeniowego do typu arytmetycznego wymaga jawnego rzutowania. Tak na przykład, biorąc pod uwagę

```
void f( int );
```

jako metodę nieprzeciążoną w wywołaniu zarządzanych rozszerzeń

```
f( rslt ); // ok: Managed Extensions; error: new syntax
```

ok, a wartość znajdująca się w obrębie `rslt` jest niejawnie konwertowany na wartość całkowitą. W programie Visual C++ to wywołanie nie zostanie skompilowany. Aby poprawnie przetłumaczyć go, firma Microsoft Wstaw operatora konwersji:

```
f( safe_cast<int>( rslt )); // ok: new syntax
```

## <a name="the-scope-of-the-clr-enum-type"></a>Zakres typ wyliczenia CLR

Jeden z zmiany między językami C i C++ jest dodanie w języku C++ zakresu w obrębie struktury obiektu. W języku C struktura jest po prostu danych agregacji bez obsługi interfejsu lub skojarzone zakresie. To była bardzo radykalnej zmiany w czasie i została sporne problem dla wielu nowych użytkowników C++ pochodzące z języka C. Relacja między natywnym i wyliczenia CLR jest podobny.

W zarządzanych rozszerzeń podjęto do definiowania słabo wprowadzonego nazwy modułów wyliczających wyliczenia CLR w celu symulowania braku zakresie w natywnym wyliczeniem. To nie potwierdzić pomyślne. Problem polega na tym, że powoduje to, że moduły wyliczające do zostaną przeniesione do globalnej przestrzeni nazw, co trudne do zarządzania konfliktów nazw. W nowej składni firma Microsoft ma były zgodne na inne języki CLR w obsłudze zakresów w ramach wyliczenia CLR.

Oznacza to, że każde użycie niekwalifikowanej modułu wyliczającego wyliczenia CLR nie zostanie rozpoznana przez nowej składni. Spójrzmy na przykład rzeczywistych.

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

Używa wszystkich trzech niekwalifikowanych nazw modułu wyliczającego (`(1)`, `(2)`, i `(3)`) musi być kwalifikowana w tłumaczeniu do nowej składni, aby kod źródłowy do skompilowania. Poniżej przedstawiono prawidłowe tłumaczenia oryginalnego kodu źródłowego:

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

Spowoduje to zmianę strategii projektowania między natywny i wyliczenia CLR. Wyliczenia CLR, utrzymywanie skojarzone zakresie, w programie Visual C++ jest konieczne ani skuteczne do hermetyzacji deklaracji wyliczenia w obrębie klasy. Tego idiomu ewoluował zbliżonym do momentu cfront 2.0 w laboratoriach dzwonka również w celu rozwiązania problemu zanieczyszczeniu globalne nazwę.

Oryginalne wydanie beta nową bibliotekę iostream przez Jerry Schwarz w laboratoriach dzwonka, Jerry nie hermetyzacji wszystkie skojarzone, określony dla biblioteki i wspólnego moduły wyliczające, takie jak typy wyliczeniowe `read`, `write`, `append`i tak dalej , uniemożliwił niemal służący do kompilowania ich istniejącego kodu. Jednym rozwiązaniem byłoby mangle nazwy, takie jak `io_read`, `io_write`itp. Drugim rozwiązaniem byłoby Aby zmodyfikować język, dodając zakres do wyliczenia, ale nie jest to możliwe w czasie. Środkowy rozwiązanie było do hermetyzacji typu wyliczeniowego w ramach klasy lub klas w hierarchii, gdzie nazwa tagu i moduły wyliczające wyliczenia wypełnić otaczający zakres klasy). Oznacza to, motywy umieszczenie Typy wyliczeniowe w ramach klas, co najmniej początkowo nie filozoficzne, ale praktyczne odpowiedzi na problem globalnego zanieczyszczenie przestrzeni nazw.

Wyliczenia Visual C++ nie ma już istotne korzyści enkapsulacji wyliczenia w obrębie klasy. W rzeczywistości, jeśli spojrzysz na `System` przestrzeni nazw, zostanie wyświetlony tego wyliczenia, klasy i interfejsy której z tą samą przestrzenią deklaracji.

## <a name="see-also"></a>Zobacz też

[Typy wartości i ich zachowania (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Klasa wyliczeniowa](../windows/enum-class-cpp-component-extensions.md)