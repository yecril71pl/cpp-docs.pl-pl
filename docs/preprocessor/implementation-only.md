---
title: "implementation_only — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa9fe0e8bf3cdecbdf118219cfe91be03a85a51f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="implementationonly"></a>implementation_only
**Określonego języka C++**  
  
 Pomija generację .tlh — plik nagłówka (plik nagłówka głównej).  
  
## <a name="syntax"></a>Składnia  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten plik zawiera wszystkie deklaracje używany do udostępnienia zawartości biblioteki typów. Plik nagłówka .tli z implementacji funkcji Członkowskich otoki, zostanie wygenerowany i będzie uwzględnione w kompilacji.  
  
 Jeśli ten atrybut jest określony, zawartość nagłówka .tli jest w tej samej przestrzeni nazw, zwykle używany w nagłówku danych .tlh —. Ponadto funkcje Członkowskie nie są deklarowane jako jako śródwierszowej.  
  
 `implementation_only` Atrybut jest przeznaczony do użycia w połączeniu z [no_implementation —](../preprocessor/no-implementation.md) atrybut nimi implementacje poza pliku prekompilowanego nagłówka (PCH). `#import` Instrukcji z `no_implementation` atrybutu znajduje się w regionie źródłowy użyty do utworzenia PCH. Wynikowa PCH jest używany przez wiele plików źródłowych. `#import` Instrukcji z `implementation_only` poza PCH region jest następnie używany atrybut. Jest wymagane, aby użyć tej instrukcji tylko raz w jednym z plików źródłowych. Spowoduje to wygenerowanie wszystkie funkcje Członkowskie wymagane otoki bez dodatkowych ponownej kompilacji dla każdego pliku źródłowego.  
  
> [!NOTE]
>  `implementation_only` Atrybutu w jednym `#import` instrukcja musi być używany w połączeniu z inną `#import` instrukcji tego samego typu biblioteki, z `no_implementation` atrybutu. W przeciwnym razie zostanie wygenerowany błędy kompilatora. To dlatego definicje klas otoki wygenerowane przez `#import` instrukcji z `no_implementation` atrybut jest wymagany do kompilacji wdrożoną przez `implementation_only` atrybutu.  
  
 KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)