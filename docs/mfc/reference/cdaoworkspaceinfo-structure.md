---
title: CDaoWorkspaceInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271557"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo — Struktura

`CDaoWorkspaceInfo` Struktura zawiera informacje dotyczące obszaru roboczego zdefiniowanego dla dostępu do danych dostęp do obiektów (DAO) bazy danych.

## <a name="syntax"></a>Składnia

```
struct CDaoWorkspaceInfo
{
    CString m_strName;           // Primary
    CString m_strUserName;       // Secondary
    BOOL m_bIsolateODBCTrans;    // All
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Unikatowej nazwy obiektu obszaru roboczego. Aby bezpośrednio pobrać wartość tej właściwości, należy wywołać obiekt querydef [getname —](../../mfc/reference/cdaoquerydef-class.md#getname) funkcja elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

*m_strUserName*<br/>
Wartość, która reprezentuje właściciel obiektu obszaru roboczego. Aby uzyskać powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w Pomocy programu DAO.

*m_bIsolateODBCTrans*<br/>
Wartość, która wskazuje, czy wiele transakcji, które dotyczą tej samej bazy danych ODBC są izolowane. Aby uzyskać więcej informacji, zobacz [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Aby uzyskać powiązane informacje zobacz temat "IsolateODBCTrans Property" w Pomocy programu DAO.

## <a name="remarks"></a>Uwagi

Obszar roboczy jest obiektem klasy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) funkcja elementu członkowskiego w klasie `CDaoWorkspace`.

Informacje o pobrane przez [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) funkcja członkowska jest przechowywany w `CDaoWorkspaceInfo` struktury. `CDaoWorkspaceInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoWorkspaceInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)
