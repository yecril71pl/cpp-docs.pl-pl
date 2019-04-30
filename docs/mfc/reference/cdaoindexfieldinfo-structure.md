---
title: CDaoIndexFieldInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: d03a6f6eadd4cf6ccb5279edf18675605d0b1485
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399762"
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

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
