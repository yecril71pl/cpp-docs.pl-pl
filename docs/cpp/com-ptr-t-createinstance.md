---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 2ec4e90c8f0c1009cc47e9022a09b3b8f7dbb284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190004"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Specyficzne dla firmy Microsoft**

Tworzy nowe wystąpienie obiektu danego `CLSID` lub `ProgID`.

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
`CLSID` obiektu.

*clsidString*<br/>
Ciąg Unicode, który zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`.

*clsidStringA*<br/>
Ciąg wielobajtowy przy użyciu strony kodowej ANSI, która zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`.

*dwClsContext*<br/>
Kontekst do uruchamiania kodu wykonywalnego.

*pOuter*<br/>
Nieznana zewnętrzna do [agregacji](../atl/aggregation.md).

## <a name="remarks"></a>Uwagi

Te funkcje członkowskie wywołują `CoCreateInstance` w celu utworzenia nowego obiektu COM, a następnie zapytania dla tego typu interfejsu wskaźnika inteligentnego. Wskaźnik wyników jest następnie hermetyzowany w tym obiekcie `_com_ptr_t`. `Release` jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika. Ta procedura zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.

- **CreateInstance (**  *rclsid* **,**  *dwClsContext*  **)** Tworzy nowe uruchomione wystąpienie obiektu danego `CLSID`.

- **CreateInstance (**  *clsidString* **,**  *dwClsContext*  **)** Tworzy nowe uruchomione wystąpienie obiektu o podanym ciągu Unicode, który zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`.

- **CreateInstance (**  *clsidStringA* **,**  *dwClsContext*  **)** Tworzy nowe uruchomione wystąpienie obiektu o podanym ciągu znaków wielobajtowych, który zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`. Wywołuje [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), w którym zakłada się, że ciąg znajduje się na stronie kodowej ANSI, a nie na stronie kodowej OEM.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
