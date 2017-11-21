---
title: "Hstring::hstring — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs: C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a598b6a4b0e1b6077e2232131814192ef0a81863
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Hstring — klasa](../windows/hstring-class.md)