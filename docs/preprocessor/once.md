---
title: Po | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.once
- once_CPP
dev_langs:
- C++
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b0e0b2b3667d4a33709caa643e4d26ed70b2990
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="once"></a>once
Określa, że plik zostanie dołączony (otwarte) tylko raz przez kompilator podczas kompilowania pliku kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma once  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Korzystanie z `#pragma once` można zmniejszyć czasy kompilacji, ponieważ kompilator nie będą otwierane i odczytać pliku po pierwszym #include w jednostce tłumaczenia pliku. Jest to określane jako *optymalizacji obejmują wiele*. Jest efekt jest podobny do *#include guard* idiom, używanym w definicji makro preprocesora zapobiegające wielu włączenia zawartość pliku. Ponadto pozwala to zapobiec naruszeń *reguły jednej definicji*— to wymaganie, że wszystkie szablony: typy, funkcje i obiekty ma nie więcej niż jedną definicję w kodzie.  
  
 Na przykład:  
  
```  
// header.h  
#pragma once  
// Code placed here is included only once per translation unit  
  
```  
  
 Firma Microsoft zaleca `#pragma once` dyrektywy dla nowego kodu, ponieważ nie charakteryzują się globalnej przestrzeni nazw z symbol preprocesora. Wymaga mniej wpisanie, jest mniej rozpraszać i nie może spowodować konflikty symbol — błędy spowodowane pliki nagłówkowe różnych używania tego samego symbol preprocesora jako wartość guard. Nie jest częścią standardowej C++, ale jest zaimplementowana portably przez kilka typowych kompilatory.  
  
 Nie ma żadnych dodatkowych zalet Użyj obu #include guard idiom i `#pragma once` w tym samym pliku. Kompilator rozpoznaje #include guard idiom i implementuje wielokrotność obejmują optymalizacji taki sam sposób jak `#pragma once` dyrektywy, jeśli nie komentarza-kod lub dyrektywy preprocesora pochodzi przed lub po standardowy formularz idiom:  
  
```  
// header.h  
// Demonstration of the #include guard idiom.  
// Note that the defined symbol can be arbitrary.  
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_  
#define HEADER_H_  
// Code placed here is included only once per translation unit  
#endif // HEADER_H_  
  
```  
  
 Firma Microsoft zaleca #include guard idiom, gdy kod musi być przenośne do kompilatorów, które nie implementują `#pragma once` dyrektywy, aby zachować spójność z istniejącym kodem, lub gdy obejmują wiele Optymalizacja jest niemożliwe. Taka sytuacja może wystąpić w złożonych projektów aliasu systemu plików lub aliasem zawierają ścieżki zapobiec kompilatora z identyfikowanie identyczne pliki dołączane przez kanonicznej ścieżki.  
  
 Nie można więc użyć `#pragma once` lub #include guard idiom pliki nagłówkowe, opracowane w celu uwzględnienia wiele razy przy użyciu symboli preprocesora do kontrolowania ich skutki. Na przykład w tym projekcie zobacz \<assert.h > pliku nagłówka. Również należy uważać, aby zarządzać dodać ścieżki do Unikaj tworzenia wielu ścieżek do załączone pliki, które może pokonać optymalizacji dla obu obejmują wiele #include osłony i `#pragma once`.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)