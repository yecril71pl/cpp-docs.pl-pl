---
title: Cdaoindexfieldinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1593ad1997baf0b5ce262f3177f0f063b49cec6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378647"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo — Struktura

`CDaoIndexFieldInfo` Struktura zawiera informacje dotyczące obiektu pola indeksu zdefiniowany dla obiektów dostępu do danych (DAO).

## <a name="syntax"></a>Składnia

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Unikatowej nazwy obiektu pola indeksu. Aby uzyskać szczegółowe informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

*m_bDescending*<br/>
Wskazuje indeks kolejność zdefiniowane przez obiekt indeksu. Wartość TRUE, jeśli kolejność jest malejącej.

## <a name="remarks"></a>Uwagi

Każdy indeks obiekt może mieć kilka pól, wskazując pola, które tabledef (lub zestaw rekordów na podstawie tabeli) jest indeksowana na. Odwołania do podstawowym powyższych wskazują, jak informacje są zwracane `m_pFieldInfos` członkiem [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) można uzyskać przez wywołanie obiektu `GetIndexInfo` funkcji składowej klasy typu [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Obiekty indeksu i pola indeksu nie są reprezentowane przez klasę MFC. Zamiast tego należy obiekt DAO obiektów podstawowych obiektów klasy MFC [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) zawiera kolekcję obiektów indeksu o nazwie kolekcja indeksy. Każdy obiekt indeks, z kolei zawiera kolekcję obiektów pola. W ramach tych zajęć, podaj dostępu poszczególne informacje indeks do elementów członkowskich lub uzyskiwaniu dostępu do nich w całości z `CDaoIndexInfo` obiektu przez wywołanie metody `GetIndexInfo` funkcja elementu członkowskiego krawędzi zawierającego go obiektu. `CDaoIndexInfo` Obiektu, to znaczy, ma składową danych `m_pFieldInfos`, który wskazuje na tablicę `CDaoIndexFieldInfo` obiektów.

Wywołaj `GetIndexInfo` funkcji składowej typu zawierającego obiekt tabledef lub zestawu rekordów, w której indeksy kolekcja jest przechowywany obiekt indeksu Cię interesuje. Następnie uzyskać dostęp do `m_pFieldInfos` członkiem [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) obiektu. Długość `m_pFieldInfos` tablicy jest przechowywany w `m_nFields`. `CDaoIndexFieldInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoIndexFieldInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

