---
title: nothrow (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: nothrow_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82370900fc96c97665cb35351605db86c9ff4faf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nothrow-c"></a>nothrow (C++)
**Dotyczące firmy Microsoft**  
  
 A `__declspec` rozszerzonych atrybutów, które mogą być używane w deklaracji funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten atrybut informuje kompilator, że zadeklarowanej funkcji i funkcji wywoływanych przez nią nigdy nie zgłoszenia wyjątku. Z wyjątkiem synchroniczne obsługi modelu, a teraz domyślne, kompilator można wyeliminować mechanika śledzenia okres istnienia niektórych obiektów unwindable w tych funkcji i znacznie zmniejszyć rozmiar kodu. Biorąc pod uwagę następujące dyrektywy preprocesora, deklaracje funkcji trzy poniżej są równoważne:  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 Przy użyciu `void __declspec(nothrow) __stdcall f2();` ma tę zaletę, które umożliwiają definicji interfejsu API, takim jak pokazano `#define` instrukcji, aby łatwo określić `nothrow` na zestaw funkcji. Trzeci deklaracji`, void __stdcall f3() throw();` jest składnia zdefiniowanych przez C++ standard.  
  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)