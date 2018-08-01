---
title: Przekazywanie argumentów i konwencje nazewnictwa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e1a6a8e837a44a966f262f581db04f1589233c8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404044"
---
# <a name="argument-passing-and-naming-conventions"></a>Przekazywanie argumentów i konwencje nazewnictwa
**Microsoft Specific**  
  
 Kompilatory języka Visual C++ umożliwiają określanie konwencje dotyczących przekazywania argumentów i zwracanie wartości między funkcjami a obiektami wywołującymi. Nie wszystkie konwencje są dostępne na wszystkich obsługiwanych platformach, a niektóre konwencje używają implementacji specyficznych dla platformy. W większości przypadków słowa kluczowe lub przełączniki kompilatora, które określają nieobsługiwaną Konwencję na konkretnej platformie są ignorowane, a domyślna Konwencja platformy jest używana.  
  
 Na x86 platformach wszystkie argumenty są rozszerzone do 32 bitów, gdy są przekazywane. Wartości zwracane są również rozszerzone do 32 bitów i zwracane w rejestrze EAX, z wyjątkiem struktur 8-bajtowych, które są zwracane w EAX. Większe struktury są zwracane w rejestrze EAX jako wskaźniki ukryte struktury zwrotu. Parametry są wypychane na stosie od prawej do lewej. Struktury, które nie są zasobników nie zostaną zwrócone w rejestrach.  
  
 Kompilator generuje prologu i epilogu do zapisywania i przywracania rejestrów ESI, EDI, EBX i EBP rejestruje, jeśli są one używane w funkcji.  
  
> [!NOTE]
>  Gdy struktura, Unia lub klasa jest zwracany przez funkcję według wartości, wszystkie definicje tego typu muszą być takie same, w przeciwnym razie program może zakończyć się niepowodzeniem w czasie wykonywania.  
  
 Aby uzyskać informacje dotyczące sposobu definiowania własnego kodu prologu i epilogu funkcji, zobacz [wywołania funkcji "naked"](../cpp/naked-function-calls.md).  
  
 Aby uzyskać informacje o domyślnych konwencjach wywoływania w kodzie, które elementy docelowe x64 platform, zobacz [Przegląd x64 Konwencje wywoływania](../build/overview-of-x64-calling-conventions.md). Aby uzyskać informacje o problemach z Konwencją wywoływania w kodzie, który jest przeznaczony dla platform ARM, zobacz [typowe Visual C++ ARM problemy przy migracji](../build/common-visual-cpp-arm-migration-issues.md).  
  
 Poniższe konwencje wywoływania są obsługiwane przez kompilator Visual C/C++.  
  
|Słowo kluczowe|Oczyszczanie stosu|Przekazywanie parametru|  
|-------------|-------------------|-----------------------|  
|[__cdecl](../cpp/cdecl.md)|Obiekt wywołujący|Przesuwa parametry w stosie, w odwrotnej kolejności (od prawej do lewej)|  
|[__clrcall](../cpp/clrcall.md)|n/d|Obciążenie parametrów na stosie wyrażenia CLR w kolejności (od lewej do prawej).|  
|[__stdcall](../cpp/stdcall.md)|/ / Wywoływany|Przesuwa parametry w stosie, w odwrotnej kolejności (od prawej do lewej)|  
|[__fastcall](../cpp/fastcall.md)|/ / Wywoływany|Przechowywane w rejestrach, następnie wypychane na stos|  
|[__thiscall](../cpp/thiscall.md)|/ / Wywoływany|Przesunięty na stosie; **to** wskaźnika przechowywania w ECX|  
|[__vectorcall](../cpp/vectorcall.md)|/ / Wywoływany|Przechowywane w rejestrach, następnie wypychane na stos w odwrotnej kolejności (od prawej do lewej)|  
  
 Aby uzyskać powiązane informacje, zobacz [przestarzałe Konwencje wywoływania](../cpp/obsolete-calling-conventions.md).  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Konwencje wywoływania](../cpp/calling-conventions.md)