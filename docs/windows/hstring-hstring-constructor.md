---
title: Hstring::hstring — Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3188e137d3a39fb26ca4151f72073306038e46f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876881"
---
# <a name="hstringhstring-constructor"></a>HString::HString — Konstruktor
Inicjuje nowe wystąpienie klasy HString.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `hstr`  
 Dojście HSTRING.  
  
 `other`  
 Istniejący obiekt HString.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje nowy obiekt HString, który jest pusty.  
  
 Drugi Konstruktor inicjuje nowy obiekt HString wartości istniejącej `other` parametr, a następnie niszczy `other` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)