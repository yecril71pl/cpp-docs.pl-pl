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
ms.openlocfilehash: dd2ce820367b15cb5dad8baf691a835499457a55
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870770"
---
# <a name="comptrreset"></a>ComPtr::Reset
Zwalnia wszystkie odwołania dla wskaźnika interfejsu, który jest skojarzony z tym comptr —.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba odwołań dopuszczone, jeśli istnieje.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)