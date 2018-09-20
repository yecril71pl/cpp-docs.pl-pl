---
title: Śledzenie dojścia do wartości spakowanej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7e26efae93b509700c3bb0c992d9f397559e99f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380734"
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Śledzenie dojścia do wartości spakowanej

Użycie śledzenie dojścia do typu wartości odwołania został zmieniony z zarządzanych rozszerzeń dla języka C++ do Visual C++.

OPAKOWYWANIE to cecha system typów ujednoliconego środowiska CLR. Typy wartości bezpośrednio zawierają ich stan typów referencyjnych są niejawne pary: nazwanych jednostek jest uchwytem do nienazwane obiekt przydzielony na stosie zarządzanym. Wszelkie inicjowania lub przypisania wartości typ `Object`, na przykład wymaga umieszczone typu wartości w stercie CLR — jest to gdzie pojawia się obraz konwersja boxing go - najpierw poprzez przydzielanie pamięci skojarzony, a następnie kopiując stan typu wartości , a następnie powrotu adres tego anonimowe hybrydowego wartości/odwołania. W związku z tym, kiedy zapisu w języku C#

```cpp
object o = 1024; // C# implicit boxing
```

jest znacznie bardziej dzieje niż sygnalizowane, prostota kodu. Projekt C# powoduje ukrycie złożoności, nie tylko operacje, które pojawiają się pod maską, ale także abstrakcji konwersja boxing sam. Managed Extensions for C++, z drugiej strony, danych, to może doprowadzić do fałszywe poczucie wydajność, umieszcza go w fazie użytkownika, wymagając jawna instrukcja:

```cpp
Object *o = __box( 1024 ); // Managed Extensions explicit boxing
```

OPAKOWYWANIE to niejawna w programie Visual C++:

```cpp
Object ^o = 1024; // new syntax implicit boxing
```

`__box` — Słowo kluczowe służy najważniejsze usługi w ramach zarządzanych rozszerzeń, który jest nieobecny zgodnie z projektem w językach takich jak C# i Visual Basic: zapewnia słownictwa i śledzenie obsługi dla bezpośrednie manipulowanie spakowany wystąpienia na stosie zarządzanym. Na przykład należy wziąć pod uwagę następujące mały program:

```cpp
int main() {
   double result = 3.14159;
   __box double * br = __box( result );

   result = 2.7;
   *br = 2.17;
   Object * o = br;

   Console::WriteLine( S"result :: {0}", result.ToString() ) ;
   Console::WriteLine( S"result :: {0}", __box(result) ) ;
   Console::WriteLine( S"result :: {0}", br );
}
```

Podstawowy kod generowany dla trzech wywołań `WriteLine` różne koszty dostępu do wartości spakowanej wartość wpisz (dzięki Yves Dolce dla wskazywanie tych różnic), gdzie wskazanymi wierszami Pokaż narzut związany z każdą show wywołania.

```cpp
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;
ldstr      "result :: {0}"
ldloca.s   result  // ToString overhead
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead
call       void [mscorlib]System.Console::WriteLine(string, object)

// Console::WriteLine( S"result :: {0}", __box(result) ) ;
Ldstr    " result :: {0}"
ldloc.0
box    [mscorlib]System.Double // box overhead
call    void [mscorlib]System.Console::WriteLine(string, object)

// Console::WriteLine( S"result :: {0}", br );
ldstr    "result :: {0}"
ldloc.0
call     void [mscorlib]System.Console::WriteLine(string, object)
```

Przekazywanie bezpośrednio do opakowanym typem wartościowym `Console::WriteLine` eliminuje konieczność wywołania i pakowania `ToString()`. (Oczywiście istnieje wcześniej pakowania zainicjować `br`, więc nie niczego ich chyba, że naprawdę umieściliśmy `br` do pracy.

W nowej składni obsługę spakowane typy wartości jest znacznie bardziej elegancki i zintegrowane w ramach typu systemu przy zachowaniu jego możliwości. Na przykład Oto translacji starszych mały program:

```cpp
int main()
{
   double result = 3.14159;
   double^ br = result;
   result = 2.7;
   *br = 2.17;
   Object^ o = br;
   Console::WriteLine( "result :: {0}", result.ToString() );
   Console::WriteLine( "result :: {0}", result );
   Console::WriteLine( "result :: {0}", br );
}
```

## <a name="see-also"></a>Zobacz też

[Typy wartości i ich zachowania (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)