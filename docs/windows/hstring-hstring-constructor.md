---
title: HString::HString, Konstruktor | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 96b77ec87e3219206d353f56293fc201c46f5d7e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568774"
---
# <a name="hstringhstring-constructor"></a>HString::HString — Konstruktor
Inicjuje nowe wystąpienie klasy **HString** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *HSTR*  
 Dojścia HSTRING.  
  
 *other*  
 Istniejące **HString** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje nową **HString** obiektu, który jest pusty.  
  
 Drugi Konstruktor inicjuje nowe **HString** obiektu do wartości istniejących *innych* parametru i następnie niszczy *innych* parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)