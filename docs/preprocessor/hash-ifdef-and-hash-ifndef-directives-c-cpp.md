---
title: '#<a name="ifdef-and-ifndef-directives-cc--microsoft-docs"></a>Dyrektywy ifdef i #ifndef (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs: C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7a56212dc0943c79152b8485bea3a3082bfa73d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 **Dotyczące firmy Microsoft**  
  
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