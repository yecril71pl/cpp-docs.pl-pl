---
title: ComPtr::Reset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74f26f520be276de863c612718de8520bffc1219
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649708"
---
# <a name="comptrreset"></a>ComPtr::Reset
Zwalnia wszystkie odwołania dla wskaźnika do interfejsu, który jest skojarzony z tym **ComPtr**.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba odwołań do wydania, jeśli istnieje.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)