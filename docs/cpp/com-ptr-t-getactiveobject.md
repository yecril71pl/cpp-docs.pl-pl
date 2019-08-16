---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498894"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft Specific**

Dołącza do istniejącego wystąpienia obiektu danego a `CLSID` lub. `ProgID`

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
Ciąg Unicode, który zawiera `CLSID` (Zaczynając od " **{** `ProgID`") lub.

*clsidStringA*<br/>
Ciąg wielobajtowy przy użyciu strony kodowej ANSI, która zawiera `CLSID` (Zaczynając od " **{** `ProgID`") lub.

## <a name="remarks"></a>Uwagi

Te funkcje członkowskie wywołują metodę GetActiveObject, aby pobrać wskaźnik do uruchomionego obiektu, który został zarejestrowany za pomocą OLE, a następnie wysyła zapytanie dla tego typu interfejsu wskaźnika inteligentnego. Wskaźnik wyników jest następnie hermetyzowany w obrębie tego `_com_ptr_t` obiektu. `Release`jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika. Ta procedura zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.

- **GetActiveObject (** `rclsid` **)** dołącza do istniejącego wystąpienia obiektu danego a `CLSID`.

- **GetActiveObject (** `clsidString` **)** dołącza do istniejącego wystąpienia obiektu, w którym znajduje się `CLSID` ciąg Unicode, który zawiera ( `ProgID`Zaczynając od " **{** ") lub.

- **GetActiveObject (** `clsidStringA` **)** dołącza do istniejącego wystąpienia obiektu, w którym znajduje się `CLSID` ciąg znaków wielobajtowych, który zawiera ( `ProgID`Zaczynając od " **{** ") lub. Wywołuje [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), w którym zakłada się, że ciąg znajduje się na stronie kodowej ANSI, a nie na stronie kodowej OEM.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)