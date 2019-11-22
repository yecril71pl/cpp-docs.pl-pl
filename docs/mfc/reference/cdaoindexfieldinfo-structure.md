---
title: CDaoIndexFieldInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303668"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo — Struktura

Struktura `CDaoIndexFieldInfo` zawiera informacje o obiekcie pola indeksu zdefiniowanym dla obiektów dostępu do danych (DAO).

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

Obiekt indeksu może mieć liczbę pól wskazującą, które pola tabledef (lub zestaw rekordów na podstawie tabeli) są indeksowane. Odwołania do elementu głównego powyżej wskazują, w jaki sposób informacje są zwracane w `m_pFieldInfos` elemencie członkowskim obiektu [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) uzyskanym przez wywołanie `GetIndexInfo` funkcji składowej klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Obiekty indeksu i obiekty pól indeksów nie są reprezentowane przez klasę MFC. Zamiast tego obiekty DAO powiązane z obiektami MFC klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) zawierają kolekcję obiektów indeksu o nazwie kolekcja indeksów. Każdy obiekt indeksu z kolei zawiera kolekcję obiektów pól. Te klasy dostarczają funkcje członkowskie, aby uzyskać dostęp do poszczególnych elementów informacji o indeksie, lub można uzyskać do nich dostęp jednocześnie przy użyciu obiektu `CDaoIndexInfo`, wywołując funkcję członkowską `GetIndexInfo` obiektu zawierającego. Obiekt `CDaoIndexInfo`, a następnie ma element członkowski danych `m_pFieldInfos`, który wskazuje na tablicę obiektów `CDaoIndexFieldInfo`.

Wywołaj `GetIndexInfo` funkcję członkowską zawierającą obiekt tabledef lub zestaw rekordów, w której kolekcja indeksów jest przechowywana obiektu indeksu, który Cię interesuje. Następnie uzyskaj dostęp do `m_pFieldInfos` elementu członkowskiego obiektu [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) . Długość tablicy `m_pFieldInfos` jest przechowywana w `m_nFields`. `CDaoIndexFieldInfo` również definiuje funkcję członkowską `Dump` w kompilacjach debugowania. Aby zrzucić zawartość obiektu `CDaoIndexFieldInfo`, można użyć `Dump`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
