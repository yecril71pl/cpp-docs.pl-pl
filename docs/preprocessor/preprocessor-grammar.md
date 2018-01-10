---
title: Gramatyka preprocesora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 797d4bf4274a92ca4f265d01579698c0f9c6a4a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="preprocessor-grammar"></a>Gramatyka preprocesora
**#define***identyfikator* *ciąg tokenu*opcjonalnych  
  
 *#***zdefiniować***identyfikator*[**(** *identyfikator*opt**,** *...*  **,** *identyfikator*opt **)**] *ciąg tokenu*opcjonalnych  
  
 **Definicja (***identyfikator* **)**   
  
 **definicja***identyfikator*   
  
 `#include`**"***ścieżka spec***"**  
  
 `#include` **\<**  *ścieżka spec***>**  
  
 **#line***sekwencji cyfr***"** *filename* **"**opcjonalnych  
  
 *#***undef***identyfikator*   
  
 **#error***ciąg tokenu*   
  
 **#pragma***ciąg tokenu*   
  
 *warunkowe* :  
 *Jeśli część elif części*opt*część else*opt*endif wiersza*  
  
 *Jeśli część* :  
 *Jeśli linetext*  
  
 *Jeśli wiersz* :  
 **#if***wyrażenie stałej*   
  
 **#ifdef***identyfikator*   
  
 **#ifndef***identyfikator*   
  
 *elif części* :  
 *elif wiersza tekstu*  
  
 *elif części elif wiersza tekstu*  
  
 *elif — wiersz* :  
 **#elif***wyrażenie stałej*   
  
 *część else* :  
 *else linetext*  
  
 *else wiersza* :  
 `#else`  
  
 *ENDIF-line* :  
 `#endif`  
  
 *cyfra sekwencji* :  
 *cyfra*  
  
 *cyfra sekwencji cyfr*  
  
 *cyfra* : jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *ciąg tokenu* :  
 Ciąg tokenów  
  
 *Token* :  
 *słowo kluczowe*  
  
 *Identyfikator*  
  
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