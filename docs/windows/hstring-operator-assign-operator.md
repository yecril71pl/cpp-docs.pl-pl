---
title: "HString::Operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs: C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5abaa00030b301607c19def42920cb01eb72600a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hstringoperator-operator"></a>HString::Operator= Operator
Przenosi bieżący obiekt HString wartość innego obiektu HString.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Istniejący obiekt HString.  
  
## <a name="remarks"></a>Uwagi  
 Wartość istniejącej `other` obiektu jest kopiowany do bieżącego obiektu HString, a następnie `other` obiekt zostanie zniszczony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)