---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 82b180b3f40683495ed2cfa284bdae8e1afaef9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498663"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft Specific**

Tworzy nowe wystąpienie obiektu `CLSID` z lub. `ProgID`

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
Ciąg Unicode, który zawiera `CLSID` (Zaczynając od " **{** `ProgID`") lub.

*clsidStringA*<br/>
Ciąg wielobajtowy przy użyciu strony kodowej ANSI, która zawiera `CLSID` (Zaczynając od " **{** `ProgID`") lub.

*dwClsContext*<br/>
Kontekst do uruchamiania kodu wykonywalnego.

*pOuter*<br/>
Nieznana zewnętrzna do [agregacji](../atl/aggregation.md).

## <a name="remarks"></a>Uwagi

Te funkcje członkowskie wywołują `CoCreateInstance` do utworzenia nowego obiektu com, a następnie zapytania dla tego typu interfejsu wskaźnika inteligentnego. Wskaźnik wyników jest następnie hermetyzowany w obrębie tego `_com_ptr_t` obiektu. `Release`jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika. Ta procedura zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.

- **CreateInstance (** *rclsid* **,** *dwClsContext* **)** Tworzy nowe uruchomione wystąpienie obiektu danego elementu `CLSID`.

- **CreateInstance (** *clsidString* **,** *dwClsContext* **)** Tworzy nowe uruchomione wystąpienie obiektu o podanym ciągu Unicode, który zawiera `CLSID` (Zaczynając od " **{** `ProgID`") lub.

- **CreateInstance (** *clsidStringA* **,** *dwClsContext* **)** Tworzy nowe uruchomione wystąpienie obiektu o podanym ciągu znaków wielobajtowych, który zawiera `CLSID` (Zaczynając od " **{** `ProgID`") lub. Wywołuje [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), w którym zakłada się, że ciąg znajduje się na stronie kodowej ANSI, a nie na stronie kodowej OEM.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)