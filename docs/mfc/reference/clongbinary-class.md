---
title: Clongbinary — klasa
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
ms.openlocfilehash: ed3a153ec89785a9c9da43037d20f7d88b5661ff
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260715"
---
# <a name="clongbinary-class"></a>Clongbinary — klasa

Upraszcza pracę z obiektami bardzo dużych danych binarnych (często zwanymi blob lub "duże obiekty binarne") w bazie danych.

## <a name="syntax"></a>Składnia

```
class CLongBinary : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Konstruuje `CLongBinary` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Zawiera rzeczywisty rozmiar w bajtach obiektu danych, w których uchwyt jest przechowywany w `m_hData`.|
|[CLongBinary::m_hData](#m_hdata)|Zawiera wartości Windows HGLOBAL dojścia do obiektu rzeczywisty obraz.|

## <a name="remarks"></a>Uwagi

Na przykład pole rekordu w tabeli SQL może zawierać reprezentujący obraz mapy bitowej. A `CLongBinary` obiekt przechowuje takiego obiektu i przechowuje informacje o jego rozmiar.

> [!NOTE]
>  Ogólnie rzecz biorąc, lepiej jest teraz używać [CByteArray](../../mfc/reference/cbytearray-class.md) w połączeniu z [dfx_binary —](record-field-exchange-functions.md#dfx_binary) funkcji. Można nadal używać `CLongBinary`, ale ogólnie rzecz biorąc `CByteArray` dostępnych jest więcej funkcji w podsystemie Win32, ponieważ nie znajduje się już ograniczenie rozmiaru z 16-bitowych `CByteArray`. Ta informacja ma zastosowanie do programowania w języku systemu nazw domen (DAO, Data Access Objects), a także Open Database Connectivity (ODBC).

Aby użyć `CLongBinary` obiektu, deklaruje pole składowej danych typu `CLongBinary` w klasie zestawu rekordów. Ten element członkowski będzie osadzonego elementu członkowskiego klasy zestawu rekordów i zbudowane w sytuacji, gdy jest konstruowany zestawu rekordów. Po `CLongBinary` obiekt jest konstruowany, mechanizm wymiany (RFX) pola rekordów ładowania obiektów danych z pola z bieżącego rekordu w źródle danych i zapisuje go do rekordu, gdy rekord zostanie zaktualizowany. RFX zapytania źródła danych dla rozmiaru duży obiekt binarny, przydziela pamięć dla niego (za pośrednictwem `CLongBinary` obiektu `m_hData` element członkowski danych) i zapisuje `HGLOBAL` obsługi z danymi w `m_hData`. RFX przechowuje także rzeczywisty rozmiar obiektu danych w `m_dwDataLength` element członkowski danych. Praca z danymi w obiekcie za pośrednictwem `m_hData`, przy użyciu tych samych technik, które zwykle są używane do manipulowania danych przechowywanych w Windows `HGLOBAL` obsługi.

Gdy zniszczyć rekordów, osadzonego `CLongBinary` również niszczony jest obiekt i jego destruktor zwalnia `HGLOBAL` dojście do danych.

Aby uzyskać więcej informacji na temat dużych obiektów, a także korzystanie z `CLongBinary`, zobacz artykuły [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md) i [zestaw rekordów: Praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Wymagania

**Header:** afxdb_.h

##  <a name="clongbinary"></a>  CLongBinary::CLongBinary

Konstruuje `CLongBinary` obiektu.

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

Przechowuje rzeczywisty rozmiar w bajtach danych przechowywanych w wartości HGLOBAL uchwytu `m_hData`.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Uwagi

Ten rozmiar może być mniejszy niż rozmiar bloku pamięci przydzielonej dla danych. Wywołanie Win32 [funkcja GLobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize) funkcję w celu uzyskania przydzielony rozmiar.

##  <a name="m_hdata"></a>  CLongBinary::m_hData

Przechowuje wartości Windows HGLOBAL dojścia do danych rzeczywistych duży obiekt binarny.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
