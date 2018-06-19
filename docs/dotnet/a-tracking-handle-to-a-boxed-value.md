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
ms.openlocfilehash: 6d3be5a46eab68a7f02bb97c477c1ec0b7fcd54d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108292"
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Śledzenie dojścia do wartości spakowanej
Użycie śledzenie dojścia do typu wartości odwołania został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Opakowanie jest cecha typu CLR unified systemu. Typy wartości bezpośrednio zawierać ich stan, gdy typy referencyjne są parę niejawne: obiekt o nazwie jest dojścia do nazwy obiektu przydzielone na stercie zarządzanej. Inicjowanie ani przypisanie wartości typ `Object`, na przykład wymaga typu wartości będzie umieszczony sterty CLR — jest to jeżeli obraz konwersja boxing go wynika — najpierw przydzielając pamięć skojarzony, a następnie kopiując typ wartości stanu , a następnie zwracanie adresu tego anonimowego hybrydowego wartości/odwołania. W związku z tym, kiedy zapisuje jedną w języku C#  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 jest znacznie bardziej przejściem niż sygnalizowane przez prostota kodu. Projekt C# ukrywa złożoność nie tylko jakie operacje odbywają się pod maską, ale także poboru konwersja boxing sam. Rozszerzenia Managed Extensions for C++ z drugiej strony, danych, to może doprowadzić do false zorientować się, wydajność, umieszcza je w fazie użytkownika, gdyż jawna instrukcja:  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 Opakowanie jest niejawne w programie Visual C++:  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 `__box` — Słowo kluczowe służy niezbędne usługi w ramach zarządzanych rozszerzeń jest nieobecny zgodnie z projektem z języków, takich jak C# i Visual Basic: zapewnia zarówno słownictwa i śledzenie obsługi na bezpośrednie manipulowanie spakowanym wystąpieniem na stercie zarządzanej. Rozważmy na przykład małych następujący program:  
  
```  
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
  
 Kod źródłowy wygenerowany dla trzech wywołań `WriteLine` Pokaż różne koszty dostępu do wartości wartości spakowanej wpisz (dzięki użyciu Yves Dolce dla wskazujące tych różnic), gdzie wskazanymi wierszami show obciążenia związanego z każdym wywołania.  
  
```  
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
  
 Przekazanie bezpośrednio do typu wartości spakowanej `Console::WriteLine` eliminuje zarówno opakowywanie i trzeba wywołać `ToString()`. (Oczywiście istnieje wcześniejszej pakującej zainicjować `br`, dlatego firma Microsoft nie niczego uzyskania chyba, że naprawdę testujemy `br` do pracy.  
  
 W nowej składni obsługę spakowanymi typami wartości jest znacznie bardziej elegancki i zintegrowane w systemie typów przy zachowaniu jego zasilania. Na przykład w tym miejscu jest translacja wcześniejszych mały program:  
  
```  
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
 [Typy wartości i ich zachowania (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)