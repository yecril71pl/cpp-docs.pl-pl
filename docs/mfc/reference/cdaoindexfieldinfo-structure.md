---
title: CDaoIndexFieldInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: a8b0ff991b8cc4988192b89d7f70309af9b9112a
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096091"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo — Struktura

`CDaoIndexFieldInfo` Struktura zawiera informacje o obiekcie pola indeksu zdefiniowanego dla obiektów dostępu do danych (DAO).

Obiekty DAO są obsługiwane przez pakiet Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

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
Unikatowa nazwa obiektu pola indeksu. Aby uzyskać szczegółowe informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

*m_bDescending*<br/>
Wskazuje kolejność indeksowania zdefiniowaną przez obiekt index. Ma wartość TRUE, jeśli kolejność jest malejąca.

## <a name="remarks"></a>Uwagi

Obiekt indeksu może mieć liczbę pól wskazującą, które pola tabledef (lub zestaw rekordów na podstawie tabeli) są indeksowane. Odwołania do podstawowego powyżej wskazują, jak informacje są zwracane `m_pFieldInfos` w elemencie członkowskim obiektu [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) `GetIndexInfo` uzyskanym przez wywołanie funkcji składowej klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Obiekty indeksu i obiekty pól indeksów nie są reprezentowane przez klasę MFC. Zamiast tego obiekty DAO powiązane z obiektami MFC klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) zawierają kolekcję obiektów indeksu o nazwie kolekcja indeksów. Każdy obiekt indeksu z kolei zawiera kolekcję obiektów pól. Te klasy dostarczają funkcje członkowskie, aby uzyskać dostęp do poszczególnych elementów informacji o indeksie, lub można uzyskać do nich dostęp `CDaoIndexInfo` jednocześnie przy użyciu obiektu `GetIndexInfo` , wywołując funkcję członkowską obiektu zawierającego. Obiekt,,, ma `m_pFieldInfos`element członkowski danych,, który `CDaoIndexFieldInfo` wskazuje na tablicę obiektów. `CDaoIndexInfo`

Wywołaj `GetIndexInfo` funkcję członkowską zawierającego obiekt tabledef lub Recordset, w której kolekcja indeksów jest przechowywana obiektu indeksu, który Cię interesuje. Następnie uzyskaj dostęp `m_pFieldInfos` do elementu członkowskiego obiektu [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) . Długość `m_pFieldInfos` tablicy jest przechowywana w `m_nFields`. `CDaoIndexFieldInfo`definiuje również funkcję `Dump` członkowską w kompilacjach debugowania. Możesz użyć `Dump` , aby zrzucić zawartość `CDaoIndexFieldInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
