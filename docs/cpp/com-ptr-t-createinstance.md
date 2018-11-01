---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: c4f6cd54b90ab5fab69f91df67a8bf60b0b658f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637466"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft Specific**

Tworzy nowe wystąpienie obiektu, biorąc pod uwagę `CLSID` lub `ProgID`.

## <a name="syntax"></a>Składnia

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Parametry

*rclsid*<br/>
`CLSID` Obiektu.

*clsidString*<br/>
Ciąg Unicode, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.

*clsidStringA*<br/>
Wielobajtowy ciąg przy użyciu stronę kodową ANSI, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.

*dwClsContext*<br/>
Kontekst do uruchamiania kodu wykonywalnego.

*pOuter*<br/>
Zewnętrzne nieznany dla [agregacji](../atl/aggregation.md).

## <a name="remarks"></a>Uwagi

Te funkcje elementów członkowskich wywołać `CoCreateInstance` Aby utworzyć nowy obiekt COM, a następnie zapytania dla typu interfejsu to inteligentny wskaźnik. Wskaźnik wynikowy następnie są hermetyzowane w ramach tej `_com_ptr_t` obiektu. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika. Ta procedura zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia.

- **CreateInstance — (***rclsid* **,***dwClsContext***)** tworzy nowe wystąpienie uruchomionego obiektu, biorąc pod uwagę `CLSID`.

- **CreateInstance — (***clsidString* **,***dwClsContext***)** tworzy nowe wystąpienie uruchomionej danego obiektu Ciąg w formacie Unicode, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.

- **CreateInstance — (***clsidStringA* **,***dwClsContext***)** tworzy nowe wystąpienie uruchomionej danego obiektu ciąg znaków wielobajtowych, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`. Wywołania [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), która zakłada, że ten ciąg jest w stronę kodową ANSI zamiast stronę kodową OEM.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)