---
title: implementation_only — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e7f0f40ad5d01b647f1f3273dc9a55d7cfa7564
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464450"
---
# <a name="implementationonly"></a>implementation_only
**Określonego język C++**  
  
Powoduje pominięcie generowania pliku nagłówku .tlh (główny plik nagłówka).  
  
## <a name="syntax"></a>Składnia  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>Uwagi  
 
Ten plik zawiera wszystkie deklaracje używany do udostępnienia zawartość biblioteki typów. .Tli pliku nagłówka, z implementacjami funkcje Członkowskie otoki, zostanie wygenerowany i uwzględniony w kompilacji.  
  
Jeśli ten atrybut jest określony, zawartość nagłówka .tli znajduje się w tej samej przestrzeni nazw jest zwykle używana w nagłówku .tlh. Ponadto funkcje elementów członkowskich nie są deklarowane jako wbudowane.  
  
**Implementation_only —** atrybut jest przeznaczony do użycia w połączeniu z [no_implementation —](../preprocessor/no-implementation.md) atrybutu jako sposób na utrzymanie implementacje z pliku wstępnie skompilowanego nagłówka (PCH). `#import` Instrukcję, określając `no_implementation` atrybut jest umieszczany w regionie źródłowym użyty do utworzenia PCH. Wynikowy PCH jest używany przez wiele plików źródłowych. `#import` Instrukcję, określając **implementation_only —** atrybutu jest następnie używany poza regionem PCH. Jest wymagane, aby użyć tej instrukcji tylko raz w jednym z plików źródłowych. Spowoduje to wygenerowanie wszystkie funkcje składowe wymagane otoki bez dodatkowych ponownej kompilacji dla każdego pliku źródłowego.  
  
> [!NOTE]
> **Implementation_only —** atrybutu w jednym `#import` instrukcja musi być używany w połączeniu z innego `#import` instrukcji tego samego wpisz biblioteki, za pomocą `no_implementation` atrybutu. W przeciwnym razie zostaną wygenerowane błędy kompilatora. Jest to spowodowane definicje klas otoki wygenerowane przez `#import` instrukcję, określając `no_implementation` atrybutu są wymagane do kompilowania wdrożoną przez **implementation_only —** atrybutu.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)