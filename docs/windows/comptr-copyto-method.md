---
title: ComPtr::CopyTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9b84cbcc970183222ed06752dc61b5672615868
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405388"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo — Metoda

Kopiuje skojarzony z tym interfejs bieżącej lub określonej **ComPtr** określony wskaźnik.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Nazwa typu.

*ptr*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik do żądanego interfejsu.

*Parametr riid*<br/>
Identyfikator interfejsu.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje, dlaczego niejawny `QueryInterface` operacja nie powiodła się.

## <a name="remarks"></a>Uwagi

Pierwsza funkcja zwraca kopię wskaźnika do interfejsu, który został skojarzony z tym **ComPtr**. Ta funkcja zawsze zwraca wartość S_OK.

Druga funkcja wykonuje `QueryInterface` operacji w interfejsie skojarzony z tym **ComPtr** dla interfejsu, określonego przez *riid* parametru.

Trzecia funkcja wykonuje `QueryInterface` operacji w interfejsie skojarzony z tym **ComPtr** dla podstawowego interfejsu *U* parametru.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ComPtr, klasa](../windows/comptr-class.md)