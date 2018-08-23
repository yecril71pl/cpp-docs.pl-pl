---
title: ClassFactory::QueryInterface, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 9593881f-4585-4d70-8ca6-b328918d4d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80c369d5ccbcc9f83d0f3ff90769a3df5d7ec177
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603415"
---
# <a name="classfactoryqueryinterface-method"></a>ClassFactory::QueryInterface — Metoda

Pobiera wskaźnik do interfejsu, określony przez parametr.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*Parametr riid*  
Identyfikator interfejsu.

*ppvObject*  
Po zakończeniu tej operacji, wskaźnik do interfejsu, określony przez parametr *riid*.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ClassFactory, klasa](../windows/classfactory-class.md)