---
title: "Semantyka stosu C++ dla typów referencyjnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f4bf38fa6512b0dc86edad43c893d2dd09a97a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-stack-semantics-for-reference-types"></a>Semantyka stosu języka C++ dla typów odwołań
Przed Visual C++ 2005, typu odwołania tylko można utworzyć wystąpienia przy użyciu `new` sterty zbierane operatora, który utworzył obiekt na odzyskiwanie. Teraz można jednak utworzyć wystąpienia typu referencyjnego przy użyciu takiej samej składni, który ma zostać użyty do utworzenia wystąpienia typu natywnego na stosie. Tak, nie trzeba używać [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) do utworzenia obiektu typu referencyjnego. Gdy obiekt poza zakresem, kompilator wywołań destruktor obiektu i.  
  
## <a name="remarks"></a>Uwagi  
 Podczas tworzenia wystąpienia typu referencyjnego, używając semantyki stosu kompilatora wewnętrznie utworzenie wystąpienia na stercie zebranych pamięci (za pomocą `gcnew`).  
  
 Jeśli podpis lub zwracany typ funkcji obejmuje wystąpienia typu referencyjnego przez wartość, funkcja zostaną oznaczone w metadanych jako wymagające specjalnej obsługi (z modreq). Ta obsługa specjalnej jest obecnie tylko udostępniane przez klientów programu Visual C++. inne języki aktualnie nie obsługują odbierającą funkcji lub dane, które używane typy referencyjne utworzone za pomocą semantyka stosu.  
  
 Jedną z przyczyn do użycia `gcnew` (dynamiczna alokacja) zamiast stosu semantyki będzie, jeśli typ ma nie ma destruktora. Ponadto przy użyciu typów referencyjnych utworzone za pomocą semantyka stosu w sygnatury funkcji nie będzie możliwe, jeśli mają być używane przez języków innych niż Visual C++ funkcji.  
  
 Kompilator nie będą generowane Konstruktor kopiujący dla typu odwołania. W związku z tym należy zdefiniować funkcję, która używa typu odwołanie według wartości w podpisie, należy zdefiniować Konstruktor kopiujący dla typu odwołania. Konstruktor kopiujący dla typu odwołania ma podpis następującą postać: `R(R%){}`.  
  
 Kompilator nie będą generowane domyślnego operatora przypisania dla typu odwołania. Operator przypisania umożliwia tworzenie obiektu przy użyciu semantyka stosu i zainicjować go z istniejącym obiektem utworzone za pomocą semantyka stosu. Operator przypisania dla typu odwołania ma podpis następującą postać: `void operator=( R% ){}`.  
  
 Semantyka stosu jest używane dla typów odniesienia destruktora danego typu zwalnia zasoby krytyczne, nie trzeba jawnie wywołać destruktor (lub zadzwoń `delete`). Aby uzyskać więcej informacji dotyczących destruktory w typach odwołań, zobacz [destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Operator przypisania generowane przez kompilator będzie wykonaj zwykle standardowe reguły C++ z następującymi dodatkami:  
  
-   Niestatyczna danych, które będą elementów członkowskich, których typ to dojścia do typu referencyjnego skrócona skopiowanych (traktowane jak element członkowski danych niestatyczna, którego typ jest wskaźnik).  
  
-   Każdy członek niestatyczna danych, którego typem jest typ wartości będą skrócona skopiowane.  
  
-   Każdy członek niestatyczna danych, którego typ jest wystąpieniem typu referencyjnego wywoła wywołanie konstruktora kopiującego typ odwołania.  
  
 Udostępnia również kompilator `%` operatora jednoargumentowego można przekonwertować wystąpienia typu referencyjnego utworzone za pomocą semantyka stosu do jego typem podstawowym dojścia.  
  
 Następujące typy odwołań nie są dostępne do użycia z semantyka stosu:  
  
-   [delegate (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md)  
  
-   [Tablice](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykładowy kod przedstawia sposób zadeklarować wystąpień typy referencyjne z semantyka stosu, jak operator przypisania i działania konstruktora kopiowania i jak zainicjować odwołaniem śledzącym z typem referencyjnym, utworzone za pomocą semantyka stosu.  
  
### <a name="code"></a>Kod  
  
```  
// stack_semantics_for_reference_types.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
   R(){}  
  
   // assignment operator  
   void operator=(R% r) {  
      i = r.i;  
   }  
  
   // copy constructor  
   R(R% r) : i(r.i) {}  
};  
  
void Test(R r) {}   // requires copy constructor  
  
int main() {  
   R r1;  
   r1.i = 98;  
  
   R r2(r1);   // requires copy constructor  
   System::Console::WriteLine(r1.i);  
   System::Console::WriteLine(r2.i);  
  
   // use % unary operator to convert instance using stack semantics  
   // to its underlying handle  
   R ^ r3 = %r1;  
   System::Console::WriteLine(r3->i);  
  
   Test(r1);  
  
   R r4;  
   R r5;  
   r5.i = 13;  
   r4 = r5;   // requires a user-defined assignment operator  
   System::Console::WriteLine(r4.i);  
  
   // initialize tracking reference  
   R % r6 = r4;  
   System::Console::WriteLine(r6.i);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
98  
98  
98  
13  
13  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)