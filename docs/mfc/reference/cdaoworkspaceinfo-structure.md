---
title: Cdaoworkspaceinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f46bfec2d74b0d1fd292b3c9852ba8ea568329a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441762"
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

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)
