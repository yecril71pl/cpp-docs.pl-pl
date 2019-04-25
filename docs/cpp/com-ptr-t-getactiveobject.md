---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: 84e43de9c40baa3c596c68ed7739471c059cbac7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154854"
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