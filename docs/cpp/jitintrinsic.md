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
ms.openlocfilehash: f8b1c932f53651b8ad116139724348714b183506
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939393"
---
# <a name="jitintrinsic"></a>jitintrinsic
Oznacza funkcję jako istotny dla 64-bitowe środowisko uruchomieniowe języka wspólnego. Jest on używany w przypadku pewnych funkcji w bibliotekach udostępnionych przez firmę Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Uwagi  
 `jitintrinsic` dodaje MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) do sygnatury funkcji.  
  
 Użytkownicy są odradzane ze za pomocą tego **__declspec** modyfikator, jako nieoczekiwane wyniki mogą wystąpić.  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)