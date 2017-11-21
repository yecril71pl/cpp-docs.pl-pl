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
ms.openlocfilehash: ec8e77d1074b3dbd10d68f205af656d7f33aa334
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Hstring — klasa](../windows/hstring-class.md)