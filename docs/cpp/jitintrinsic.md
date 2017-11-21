---
title: jitintrinsic | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 69e0350df240d4748a91b1400c1811209b9dfdd1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="jitintrinsic"></a>jitintrinsic
Oznacza funkcji jako istotne dla 64-bitowego środowiska CLR. Jest ono używane w przypadku niektórych funkcji w bibliotekach udostępnionych przez firmę Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Uwagi  
 `jitintrinsic`dodaje MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) do sygnatury funkcji.  
  
 Użytkownicy są odradzane ze za pomocą tej `__declspec` modyfikator, jako nieoczekiwane wyniki mogą wystąpić.  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)