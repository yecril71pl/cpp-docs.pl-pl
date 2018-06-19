---
title: jitintrinsic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71cd88882ea104275e4c1a43ccf05494a859d303
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418757"
---
# <a name="jitintrinsic"></a>jitintrinsic
Oznacza funkcji jako istotne dla 64-bitowego środowiska CLR. Jest ono używane w przypadku niektórych funkcji w bibliotekach udostępnionych przez firmę Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Uwagi  
 `jitintrinsic` dodaje MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) do sygnatury funkcji.  
  
 Użytkownicy są odradzane ze za pomocą tej `__declspec` modyfikator, jako nieoczekiwane wyniki mogą wystąpić.  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)