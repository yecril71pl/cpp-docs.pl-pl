---
title: _com_ptr_t::GetActiveObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9f77a894c39fc907367e5d4f8c7a687cc703331
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056511"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft Specific**

Dołącza do istniejącego wystąpienia danego obiektu `CLSID` lub `ProgID`.

## <a name="syntax"></a>Składnia

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>Parametry

*rclsid*<br/>
`CLSID` Obiektu.

*clsidString*<br/>
Ciąg Unicode, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.

*clsidStringA*<br/>
Wielobajtowy ciąg przy użyciu stronę kodową ANSI, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.

## <a name="remarks"></a>Uwagi

Wywołania tych funkcji elementów członkowskich **getactiveobject —** pobrać wskaźnika do uruchomionego obiektu, który został zarejestrowany przy użyciu OLE i następnie typ interfejsu zapytania dotyczące tej inteligentnego wskaźnika. Wskaźnik wynikowy następnie są hermetyzowane w ramach tej `_com_ptr_t` obiektu. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika. Ta procedura zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia.

- **Getactiveobject — (**`rclsid`**)** dołącza do istniejącego wystąpienia danego obiektu `CLSID`.

- **Getactiveobject — (**`clsidString`**)** dołącza do istniejącego wystąpienia obiektu, który został podany ciąg Unicode, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.

- **Getactiveobject — (**`clsidStringA`**)** dołącza do istniejącego wystąpienia obiektu, który został podany ciąg znaku wielobajtowego, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`. Wywołania [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), która zakłada, że ten ciąg jest w stronę kodową ANSI zamiast stronę kodową OEM.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)