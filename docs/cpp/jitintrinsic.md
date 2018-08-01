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
ms.openlocfilehash: f0b114089567de06a71f15b69c556e08d1e4e9c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404083"
---
# <a name="jitintrinsic"></a>jitintrinsic
Oznacza funkcję jako istotny dla 64-bitowe środowisko uruchomieniowe języka wspólnego. Jest on używany w przypadku pewnych funkcji w bibliotekach udostępnionych przez firmę Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Uwagi  
 **jitintrinsic** dodaje MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) do sygnatury funkcji.  
  
 Użytkownicy są odradzane ze za pomocą tego **__declspec** modyfikator, jako nieoczekiwane wyniki mogą wystąpić.  
  
## <a name="see-also"></a>Zobacz także  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)