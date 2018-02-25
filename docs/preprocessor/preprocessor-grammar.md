---
title: Gramatyka preprocesora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02b3597b035e3ea4bfa1670aa405109f4c01a077
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="preprocessor-grammar"></a>Gramatyka preprocesora
**#define***identyfikator* *ciąg tokenu*opcjonalnych    
  
 *#* **Zdefiniuj***identyfikator*[**(** *identyfikator*opt**,** *...*  **,** *identyfikator*opt **)**] *ciąg tokenu*opcjonalnych    
  
 **Definicja (***identyfikator* **)**   
  
 **definicja***identyfikator*   
  
 `#include` **"***path-spec***"**  
  
 `#include` **\<***path-spec***>**  
  
 **#line***sekwencji cyfr***"** *filename* **"**opcjonalnych      
  
 *#* **undef***identyfikator*   
  
 **#error***ciąg tokenu*   
  
 **#pragma***ciąg tokenu*   
  
 *warunkowe* :  
 *Jeśli część elif części*opt*część else*opt*endif wiersza*  
  
 *Jeśli część* :  
 *if-linetext*  
  
 *Jeśli wiersz* :  
 **#if**  *constant-expression*  
  
 **#ifdef***identyfikator*  
  
 **#ifndef***identyfikator*  
  
 *elif części* :  
 *elif wiersza tekstu*  
  
 *elif części elif wiersza tekstu*  
  
 *elif — wiersz* :  
 **#elif**  *constant-expression*  
  
 *część else* :  
 *else-linetext*  
  
 *else wiersza* :  
 `#else`  
  
 *ENDIF-line* :  
 `#endif`  
  
 *cyfra sekwencji* :  
 *digit*  
  
 *cyfra sekwencji cyfr*  
  
 *cyfra* : jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *ciąg tokenu* :  
 Ciąg tokenów  
  
 *Token* :  
 *keyword*  
  
 *identifier*  
  
 *Stała*  
  
 *operator*  
  
 `punctuator`  
  
 *Nazwa pliku* :  
 Nazwa pliku prawne systemu operacyjnego  
  
 *Ścieżka spec* :  
 Ścieżka pliku prawnych  
  
 *tekst* :  
 Wszelkie sekwencji tekstu  
  
> [!NOTE]
>  Następujące symboli nieterminalnych są rozwijane w [konwencje leksykalne](../cpp/lexical-conventions.md) sekcji *dokumentacja języka C++*: `constant`, `constant` - *wyrażenia* , *identyfikator*, *— słowo kluczowe*, `operator`, i `punctuator`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podsumowanie gramatyki (C/C++)](../preprocessor/grammar-summary-c-cpp.md)