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
ms.openlocfilehash: 94666c0d15898e05ae78663a15d86b7d00d5c9c6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505673"
---
# <a name="clongbinary-class"></a>Klasa CLongBinary

Upraszcza pracę z bardzo dużą ilością obiektów danych binarnych (często nazywanymi obiektami BLOB lub "dużymi obiektami binarnymi") w bazie danych.

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
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Zawiera rzeczywisty rozmiar w bajtach obiektu danych, którego dojście jest przechowywane w `m_hData`.|
|[CLongBinary::m_hData](#m_hdata)|Zawiera dojście HGLOBAL systemu Windows do rzeczywistego obiektu obrazu.|

## <a name="remarks"></a>Uwagi

Na przykład pole rekordu w tabeli SQL może zawierać mapę bitową reprezentującą obraz. `CLongBinary` Obiekt przechowuje taki obiekt i śledzi jego rozmiar.

> [!NOTE]
>  Ogólnie rzecz biorąc, lepszym rozwiązaniem jest użycie [CByteArray](../../mfc/reference/cbytearray-class.md) w połączeniu z funkcją [DFX_Binary](record-field-exchange-functions.md#dfx_binary) . Nadal można korzystać `CLongBinary`z programu, ale ogólnie `CByteArray` udostępnia więcej funkcji w systemie Win32, ponieważ nie ma już ograniczenia rozmiaru wydanego 16-bitowego `CByteArray`. Niniejsze porady dotyczą programowania z obiektami dostępu do danych (DAO) oraz Open Database Connectivity (ODBC).

Aby użyć `CLongBinary` obiektu, zadeklaruj element członkowski danych pola typu `CLongBinary` w klasie zestawu rekordów. Ten element członkowski będzie osadzonym członkiem klasy zestaw rekordów i zostanie skonstruowany podczas konstruowania zestawu rekordów. Po utworzeniu `CLongBinary` obiektu mechanizm wymiany pól rekordów (RFX) ładuje obiekt danych z pola w bieżącym rekordzie źródła danych i zapisuje go z powrotem do rekordu, gdy rekord zostanie zaktualizowany. RFX wysyła zapytanie do źródła danych dla rozmiaru dużego obiektu binarnego, przydziela `CLongBinary` magazyn dla niego (za pośrednictwem elementu członkowskiego `m_hData` danych obiektu `HGLOBAL` ) i przechowuje dojście do danych w `m_hData`. RFX również przechowuje rzeczywisty rozmiar obiektu danych w `m_dwDataLength` elemencie członkowskim danych. Pracuj z danymi w obiekcie za pośrednictwem `m_hData`, korzystając z tych samych metod, które zwykle są używane do manipulowania danymi przechowywanymi `HGLOBAL` w dojściem systemu Windows.

Gdy niszczysz zestaw rekordów, osadzony `CLongBinary` obiekt jest również niszczony, a jego destruktor cofa alokację dojścia do `HGLOBAL` danych.

Aby uzyskać więcej informacji na temat dużych obiektów i używania `CLongBinary`, zobacz [zestawy rekordów (ODBC)](../../data/odbc/recordset-odbc.md) i [zestaw rekordów: Praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb_. h

##  <a name="clongbinary"></a>CLongBinary::CLongBinary

Konstruuje `CLongBinary` obiekt.

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

Przechowuje rzeczywisty rozmiar w bajtach danych przechowywanych w obsłudze HGLOBAL w `m_hData`.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Uwagi

Rozmiar ten może być mniejszy niż rozmiar bloku pamięci przydzieloną dla danych. Wywołaj funkcję Win32 [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) , aby uzyskać przydzieloną wielkość.

##  <a name="m_hdata"></a>CLongBinary::m_hData

Przechowuje dojście HGLOBAL systemu Windows do rzeczywistych danych binarnych dużych obiektów.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
