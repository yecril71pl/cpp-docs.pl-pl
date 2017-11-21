---
title: "Przekazywanie argumentów i konwencje nazewnictwa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b9b72da1cb8da3a74334b09e4e3b99cc3cad3789
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="argument-passing-and-naming-conventions"></a>Przekazywanie argumentów i konwencje nazewnictwa
**Dotyczące firmy Microsoft**  
  
 Kompilatory języka Visual C++ pozwalają na Określ konwencjach przekazywanie argumentów i wartości zwracane pomiędzy funkcjami i obiekty wywołujące. Nie wszystkie konwencje są dostępne na wszystkich obsługiwanych platformach i niektóre konwencje użyć implementacji specyficzne dla platformy. W większości przypadków słów kluczowych lub przełączniki kompilatora, określających nieobsługiwana konwencja na konkretnej platformy są ignorowane, a platforma domyślnej konwencji jest używany.  
  
 Na x86 plaftorms, wszystkie argumenty są rozszerzone do 32-bitowy, gdy są one przekazywane. Wartości zwracane są również rozszerzeniami do 32-bitowy i zwracane w rejestrze EAX, z wyjątkiem struktur 8-bajtowych, które są zwracane w parze rejestru EDX:EAX. Większych struktur są zwracane w rejestrze EAX jako wskaźników do ukrytych zwracać struktury. Parametry są przenoszone na stosie od prawej do lewej. Struktury, które nie są stanowiskami w rejestrach nie zostaną zwrócone.  
  
 Kompilator generuje prologu i rejestruje epilogu do zapisywania i przywracania ESI, EDI, element EBX i EBP, jeśli są używane w funkcji.  
  
> [!NOTE]
>  Gdy struktura, Unią lub klasy jest zwracany przez funkcję przez wartość, wszystkie definicje typu muszą być takie same, przeciwnym razie program może zakończyć się niepowodzeniem w czasie wykonywania.  
  
 Informacje dotyczące sposobu definiowania swoim własnym kodem prolog i epilog funkcji, zobacz [wywołania funkcji Naked](../cpp/naked-function-calls.md).  
  
 Informacje o domyślne Konwencje wywoływania w kodzie, który platform docelowych x64, zobacz [omówienie x64 konwencji wywoływania](../build/overview-of-x64-calling-conventions.md). Aby dowiedzieć się, jak wywoływanie Konwencji problemów w kodzie, przeznaczonego dla platformy ARM, zobacz [typowe Visual C++ ARM problemy przy migracji](../build/common-visual-cpp-arm-migration-issues.md).  
  
 Następujących konwencji wywoływania są obsługiwane przez kompilator Visual C/C++.  
  
|Słowo kluczowe|Oczyszczanie stosu|Przekazywanie parametru|  
|-------------|-------------------|-----------------------|  
|[__cdecl](../cpp/cdecl.md)|obiekt wywołujący|Wypchnięcia parametrów na stosie, w kolejności odwrotnej (od prawej do lewej)|  
|[__clrcall](../cpp/clrcall.md)|n/d|Załadować parametrów na stosie wyrażenie CLR w kolejności (od lewej do prawej).|  
|[__stdcall](../cpp/stdcall.md)|wywoływany|Wypchnięcia parametrów na stosie, w kolejności odwrotnej (od prawej do lewej)|  
|[__fastcall](../cpp/fastcall.md)|wywoływany|Przechowywane w rejestrach, następnie wypychana na stosie|  
|[Konwencja __thiscall](../cpp/thiscall.md)|wywoływany|Wypychana na stosie; **to** przechowywane w ECX wskaźnika|  
|[__vectorcall](../cpp/vectorcall.md)|wywoływany|Przechowywane w rejestrach, następnie wypychana na stosie w odwrotnej kolejności (od prawej do lewej)|  
  
 Aby uzyskać odpowiednie informacje, zobacz [przestarzałe Konwencje wywoływania](../cpp/obsolete-calling-conventions.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje wywoływania](../cpp/calling-conventions.md)