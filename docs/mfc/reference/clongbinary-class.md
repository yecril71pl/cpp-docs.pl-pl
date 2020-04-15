---
title: Klasa CLongBinary
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370136"
---
# <a name="clongbinary-class"></a>Klasa CLongBinary

Upraszcza pracę z bardzo dużymi obiektami danych binarnych (często nazywanymi plikami BLOB lub "dużymi obiektami binarnymi") w bazie danych.

## <a name="syntax"></a>Składnia

```
class CLongBinary : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Konstruuje `CLongBinary` obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Zawiera rzeczywisty rozmiar w bajtach obiektu danych, którego uchwyt jest przechowywany w `m_hData`pliku .|
|[CLongBinary::m_hData](#m_hdata)|Zawiera uchwyt HGLOBAL systemu Windows do rzeczywistego obiektu obrazu.|

## <a name="remarks"></a>Uwagi

Na przykład pole rekordu w tabeli SQL może zawierać mapę bitową reprezentującą obraz. Obiekt `CLongBinary` przechowuje taki obiekt i śledzi jego rozmiar.

> [!NOTE]
> Ogólnie rzecz biorąc, lepiej jest teraz używać [CByteArray](../../mfc/reference/cbytearray-class.md) w połączeniu z funkcją [DFX_Binary.](record-field-exchange-functions.md#dfx_binary) Nadal można `CLongBinary`używać , `CByteArray` ale ogólnie zapewnia więcej funkcji w obszarze Win32, ponieważ nie ma `CByteArray`już ograniczenia rozmiaru napotkane z 16-bitowym . Ta porada dotyczy programowania za pomocą obiektów dostępu do danych (DAO) oraz łączności otwartej bazy danych (ODBC).

Aby użyć `CLongBinary` obiektu, należy zadeklarować `CLongBinary` element członkowski danych pola typu w klasie zestaw rekordów. Ten element członkowski będzie osadzonym członkiem klasy recordset i zostanie skonstruowany podczas konstruowania pliku recordset. Po `CLongBinary` skonstruowaniu obiektu mechanizm wymiany pól rekordów (RFX) ładuje obiekt danych z pola w bieżącym rekordzie w źródle danych i przechowuje go z powrotem do rekordu po zaktualizowaniu rekordu. RFX odpytuje źródło danych o rozmiar dużego obiektu binarnego, `CLongBinary` przydziela `m_hData` dla niego magazyn `HGLOBAL` (za pośrednictwem `m_hData`elementu członkowskiego danych obiektu) i przechowuje dojście do danych w pliku . RFX przechowuje również rzeczywisty rozmiar `m_dwDataLength` obiektu danych w elementów członkowskich danych. Praca z danymi w `m_hData`obiekcie za pośrednictwem , przy użyciu tych samych technik, `HGLOBAL` które normalnie używane do manipulowania danymi przechowywanymi w uchwycie systemu Windows.

Po zniszczeniu zestaw rekordów, `CLongBinary` obiekt osadzony jest również niszczony, a `HGLOBAL` jego destruktor przydzieli dojście danych.

Aby uzyskać więcej informacji na `CLongBinary`temat dużych obiektów i użycia programu , zobacz artykuły [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) i [Recordset: Working with Large Data Items (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary

Konstruuje `CLongBinary` obiekt.

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

Przechowuje rzeczywisty rozmiar w bajtach danych przechowywanych `m_hData`w dojście HGLOBAL w .

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Uwagi

Ten rozmiar może być mniejszy niż rozmiar bloku pamięci przydzielonego dla danych. Wywołanie funkcji Win32 [GLobalSize,](/windows/win32/api/winbase/nf-winbase-globalsize) aby uzyskać przydzielony rozmiar.

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary::m_hData

Przechowuje dojście HGLOBAL systemu Windows do rzeczywistych danych binarnych dużych obiektów.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
