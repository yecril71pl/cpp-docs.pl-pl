---
title: setLocale | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs: C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05ddb536dc4d7929141c7c153fdd9ec5ce1e9d7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setlocale"></a>setlocale
Definiuje ustawienia regionalne (Kraj/Region i język) do użycia podczas tłumaczenia — stałe znaków dwubajtowych i literały ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ algorytm Konwersja znaków wielobajtowych na znaki dwubajtowe mogą zależy od ustawień regionalnych lub kompilacja może odbywać się w różnych ustawień regionalnych, z którym zostanie uruchomiony plik wykonywalny, ta pragma zapewnia możliwość określenia ustawień regionalnych docelowej podczas kompilacji. Gwarantuje to, że ciągi znaków dwubajtowych będą przechowywane w poprawnym formacie.  
  
 Wartość domyślna *ciąg ustawień regionalnych* jest "".  
  
 Ustawienia regionalne "C" mapuje każdego znaku w ciągu na wartość jako `wchar_t` (bez znaku krótki). Inne wartości, które są prawidłowe dla `setlocale` tych wpisów, które zostały znalezione w [ciągi języka](../c-runtime-library/language-strings.md) listy. Na przykład można wystawić:  
  
```  
#pragma setlocale("dutch")  
```  
  
 Mógł wystawiać ciąg języka zależy od strony kodowej i języka obsługi identyfikatorów na tym komputerze.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)