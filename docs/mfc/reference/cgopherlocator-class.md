---
title: CGopherLocator Class
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: f25273f1d982092adc8b8010cc60818e7c0e24a2
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503667"
---
# <a name="cgopherlocator-class"></a>CGopherLocator Class

Pobiera "Lokalizator" gopher z serwera gopher, określa typ lokalizatora i udostępnia go do [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementów członkowskich są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działały na starszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Konstruuje `CGopherLocator` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analizuje lokalizatora gopher i określa jego atrybuty.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Bezpośrednio uzyskuje dostęp do znaków przechowywanych w `CGopherLocator` obiektu jako ciąg stylu C.|

## <a name="remarks"></a>Uwagi

Aplikację, musisz uzyskać lokalizatora serwera gopher, aby możliwe było pobieranie informacji z tego serwera. Gdy ma ona Lokalizator, to traktowane Lokalizator jako nieprzezroczysty token.

Lokalizator każdego gopher ma atrybuty, które określają typ pliku lub znaleziono serwera. Zobacz [GetLocatorType](#getlocatortype) listę typy lokalizatorów gopher.

Aplikacja używa zwykle Lokalizator dla wywołań [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) do pobrania konkretnych danych.

Aby dowiedzieć się więcej o tym, jak `CGopherLocator` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator

Ta funkcja członkowska jest wywoływana, aby utworzyć `CGopherLocator` obiektu.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
Odwołanie do stałej `CGopherLocator` obiektu.

### <a name="remarks"></a>Uwagi

Nigdy nie twórz `CGopherLocator` obiektu bezpośrednio. Zamiast tego należy wywołać [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) do tworzenia i zwracają wskaźnik do `CGopherLocator` obiektu.

##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać Typ lokalizatora.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parametry

*dwRef*<br/>
Odwołanie do typu DWORD, który będzie otrzymywać Typ lokalizatora. Zobacz **uwagi** dla tabeli typów lokalizatora.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Typy możliwe są następujące:

|Wartość|Znaczenie|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Plik tekstowy ASCII.|
|GOPHER_TYPE_DIRECTORY|Katalog dodatkowe elementy Gopher.|
|GOPHER_TYPE_CSO|Serwer CSO książki telefonicznej.|
|GOPHER_TYPE_ERROR|Wskazuje na błąd.|
|GOPHER_TYPE_MAC_BINHEX|Dla komputerów Macintosh pliku w formacie BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Plik archiwum systemu DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Plik zakodowany w UUENCODE.|
|GOPHER_TYPE_INDEX_SERVER|Serwer indeksu.|
|GOPHER_TYPE_TELNET|A Telnet Server.|
|GOPHER_TYPE_BINARY|Plik binarny.|
|GOPHER_TYPE_REDUNDANT|Zduplikowane serwera. Informacje zawarte w ciągu jest duplikatem podstawowego serwera. Serwer główny jest ostatni wpis katalogu, które nie mają typu GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Serwer TN3270.|
|GOPHER_TYPE_GIF|Plik grafiki GIF.|
|GOPHER_TYPE_IMAGE|Plik obrazu.|
|GOPHER_TYPE_BITMAP|Plik mapy bitowej.|
|GOPHER_TYPE_MOVIE|Plik filmu.|
|GOPHER_TYPE_SOUND|Plik dźwiękowy.|
|GOPHER_TYPE_HTML|Dokument HTML.|
|GOPHER_TYPE_PDF|Plik PDF.|
|GOPHER_TYPE_CALENDAR|Plik kalendarza.|
|GOPHER_TYPE_INLINE|Plik wbudowany.|
|GOPHER_TYPE_UNKNOWN|Typ elementu jest nieznany.|
|GOPHER_TYPE_ASK|Poproś + element.|
|GOPHER_TYPE_GOPHER_PLUS|Elementu Gopher +.|

##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR

Ten operator rzutowania przydatne zapewnia efektywną metodę dostępu zawarte w ciągu C zakończony znakiem null `CGopherLocator` obiektu.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Żadne znaki nie są kopiowane; zwracany jest tylko wskaźnikiem.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)
