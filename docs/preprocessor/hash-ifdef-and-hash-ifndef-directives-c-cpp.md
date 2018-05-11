---
title: '#Dyrektywy ifdef i #ifndef (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs:
- C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5ecfc9cc63fc4028e1f93d8f30e8d5cb9f9357
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="ifdef-and-ifndef-directives-cc"></a>Dyrektywy #ifdef i #ifndef (C/C++)
**#Ifdef** i **#ifndef** dyrektywy przeprowadzić to samo zadanie `#if` dyrektywy, gdy jest używany z **zdefiniowane**( *identyfikator* ).  
  
## <a name="syntax"></a>Składnia  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć **#ifdef** i **#ifndef** dyrektywy w dowolnym miejscu `#if` mogą być używane. **#Ifdef** *identyfikator* instrukcja jest odpowiednikiem `#if 1` podczas *identyfikator* została zdefiniowana, i jest odpowiednikiem `#if 0` podczas *identyfikator* nie została zdefiniowana lub został niezdefiniowana z `#undef` dyrektywy. Te dyrektywy Sprawdzaj tylko w obecności lub braku identyfikatory zdefiniowane z `#define`, a nie dla identyfikatorów zadeklarowany w kodzie źródłowym języka C lub C++.  
  
 Dyrektywy te są dostępne tylko dla zgodności z poprzednimi wersjami języka. **Zdefiniowane (** *identyfikator* **)** wyrażenie stałe używane z `#if` dyrektywa jest preferowany.  
  
 **#Ifndef** dyrektywy sprawdza, czy odwrotnie warunku sprawdzane przez **#ifdef**. Jeśli nie zdefiniowano identyfikatora (lub jego definicja została usunięta z `#undef`), warunek ma wartość true (różną od zera). W przeciwnym razie wynikiem warunku jest FAŁSZ (0).  
  
 **Microsoft Specific**  
  
 *Identyfikator* mogą zostać przekazane z wiersza polecenia przy użyciu opcji /D. Maksymalnie 30 makra za pomocą parametru /D.  
  
 Jest to przydatne do sprawdzania, czy istnieje definicja, ponieważ definicji mogą zostać przekazane z wiersza polecenia. Na przykład:  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)