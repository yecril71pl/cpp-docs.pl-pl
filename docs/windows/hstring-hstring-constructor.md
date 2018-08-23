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
ms.openlocfilehash: 80af8f463d6cd1af631c6cb37c0239e7a9e85c3f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595888"
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