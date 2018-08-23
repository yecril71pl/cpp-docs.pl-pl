---
title: Gramatyka preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1871d1b8281f4dd74733133ede70ed80430246b3
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464528"
---
# <a name="preprocessor-grammar"></a>Gramatyka preprocesora
**#define***identyfikator* *ciąg tokenu*zoptymalizowany pod kątem    
  
*#* **Zdefiniuj***identyfikator*[**(** *identyfikator*zoptymalizowany pod kątem **,** *...*  **,** *identyfikator*zoptymalizowany pod kątem **)**] *ciąg tokenu*zoptymalizowany pod kątem    
  
**zdefiniowany (***identyfikator* **)**   
  
**definicja***identyfikator*   
  
`#include` **"***path-spec***"**  
  
`#include` **\<***path-spec***>**  
  
**#line***sekwencję cyfr***"** *filename* **"** zoptymalizowany pod kątem      
  
*#* **undef***identyfikator*   
  
**#error***ciąg tokenu*   
  
**#pragma***ciąg tokenu*   
  
*warunkowe* :  
*część IF części elif*zoptymalizowany pod kątem*część else*zoptymalizowany pod kątem*linia endif*  
  
*część IF* :  
*if-linetext*  
  
*wiersz z operatorem IF* :  
**#if***wyrażenia stałego*   
  
**#ifdef***identyfikator*   
  
**#ifndef***identyfikator*   
  
*części elif* :  
*tekst linii elif*  
  
*tekst linii elif części elif*  
  
*Linia elif* :  
**#elif**  *constant-expression*  
  
*część else* :  
*else-linetext*  
  
*else linii* :  
`#else`  
  
*Linia ENDIF* :  
`#endif`  
  
*sekwencja cyfr* :  
*digit*  
  
*sekwencja cyfr cyfra*  
  
*cyfra* : jeden z  
**0 1 2 3 4 5 6 7 8 9**  
  
*token ciągu* :  
Ciąg tokenów  
  
*Token* :  
*keyword*  
  
*Identyfikator*  
  
*Stałe*  
  
*operator*  
  
`punctuator`  
  
*Nazwa pliku* :  
System operacyjny prawne, nazwa_pliku  
  
*PATH-spec* :  
Ścieżka pliku prawne  
  
*tekst* :  
Dowolną sekwencją tekstu  
  
> [!NOTE]
> Następujące symboli nieterminalnych są rozwijane w [konwencje leksykalne](../cpp/lexical-conventions.md) części *C++ Language Reference*: `constant`, `constant` - *wyrażenia* , *identyfikator*, *— słowo kluczowe*, `operator`, i `punctuator`.  
  
## <a name="see-also"></a>Zobacz też  
 
[Podsumowanie gramatyki (C/C++)](../preprocessor/grammar-summary-c-cpp.md)