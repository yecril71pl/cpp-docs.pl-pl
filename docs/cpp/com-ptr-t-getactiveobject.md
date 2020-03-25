---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170804"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Specyficzne dla firmy Microsoft**

Dołącza do istniejącego wystąpienia obiektu danego `CLSID` lub `ProgID`.

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
`CLSID` obiektu.

*clsidString*<br/>
Ciąg Unicode, który zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`.

*clsidStringA*<br/>
Ciąg wielobajtowy przy użyciu strony kodowej ANSI, która zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`.

## <a name="remarks"></a>Uwagi

Te funkcje członkowskie wywołują metodę **GetActiveObject** , aby pobrać wskaźnik do uruchomionego obiektu, który został zarejestrowany za pomocą OLE, a następnie wysyła zapytanie dla tego typu interfejsu wskaźnika inteligentnego. Wskaźnik wyników jest następnie hermetyzowany w tym obiekcie `_com_ptr_t`. `Release` jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika. Ta procedura zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.

- **GetActiveObject (** `rclsid` **)** Dołącza do istniejącego wystąpienia obiektu danego `CLSID`.

- **GetActiveObject (** `clsidString` **)** Dołącza do istniejącego wystąpienia obiektu danego ciągu Unicode, który zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`.

- **GetActiveObject (** `clsidStringA` **)** Dołącza do istniejącego wystąpienia obiektu, uwzględniając ciąg znaków wielobajtowych, który zawiera `CLSID` (Zaczynając od " **{** ") lub `ProgID`. Wywołuje [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), w którym zakłada się, że ciąg znajduje się na stronie kodowej ANSI, a nie na stronie kodowej OEM.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
