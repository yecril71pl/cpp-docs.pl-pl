---
title: Klasa CGopherLocator
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
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373665"
---
# <a name="cgopherlocator-class"></a>Klasa CGopherLocator

Pobiera gopher "lokalizator" z serwera gopher, określa typ lokalizatora i sprawia, że lokalizator dostępne [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
> Klasy `CGopherConnection`, `CGopherFile` `CGopherFileFind`, `CGopherLocator` i ich członkowie zostały przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą nadal działać na wcześniejszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Konstruuje `CGopherLocator` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analizuje lokalizator gopher i określa jego atrybuty.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Bezpośredni dostęp do znaków `CGopherLocator` przechowywanych w obiekcie jako ciąg w stylu C.|

## <a name="remarks"></a>Uwagi

Aplikacja musi uzyskać lokalizator serwera gopher, zanim będzie mogła pobierać informacje z tego serwera. Po jego zlokalizowaniu musi traktować lokalizator jako nieprzezroczysty token.

Każdy lokalizator gopher ma atrybuty, które określają typ znalezionego pliku lub serwera. Zobacz [GetLocatorType](#getlocatortype) listę typów lokalizatorów gopher.

Aplikacja zwykle używa lokalizatora dla wywołań [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) do pobierania określonych informacji.

Aby dowiedzieć `CGopherLocator` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

Ta funkcja elementu członkowskiego `CGopherLocator` jest wywoływana w celu utworzenia obiektu.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
Odwołanie do obiektu `CGopherLocator` stałego.

### <a name="remarks"></a>Uwagi

Nigdy nie `CGopherLocator` tworzysz obiektu bezpośrednio. Zamiast tego wywołaj [CGopherConnection::CreateLocator,](../../mfc/reference/cgopherconnection-class.md#createlocator) aby utworzyć `CGopherLocator` i zwrócić wskaźnik do obiektu.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać typ lokalizatora.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parametry

*dwRef (np.*<br/>
Odwołanie do DWORD, który otrzyma typ lokalizatora. Zobacz **Uwagi** dla tabeli typów lokalizatora.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Możliwe typy są następujące:

|Wartość|Znaczenie|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Plik tekstowy ASCII.|
|GOPHER_TYPE_DIRECTORY|Katalog dodatkowych elementów Gopher.|
|GOPHER_TYPE_CSO|Serwer książki telefonicznej CSO.|
|GOPHER_TYPE_ERROR|Wskazuje warunek błędu.|
|GOPHER_TYPE_MAC_BINHEX|Plik Macintosh w formacie BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Plik archiwum DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Plik UUENCODED.|
|GOPHER_TYPE_INDEX_SERVER|Serwer indeksu.|
|GOPHER_TYPE_TELNET|Serwer Telnet.|
|GOPHER_TYPE_BINARY|Plik binarny.|
|GOPHER_TYPE_REDUNDANT|Zduplikowany serwer. Informacje zawarte w jest duplikatem serwera podstawowego. Serwer podstawowy jest ostatnim wpisem katalogu, który nie miał typu GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Serwer TN3270.|
|GOPHER_TYPE_GIF|Plik graficzny GIF.|
|GOPHER_TYPE_IMAGE|Plik obrazu.|
|GOPHER_TYPE_BITMAP|Plik mapy bitowej.|
|GOPHER_TYPE_MOVIE|Plik filmowy.|
|GOPHER_TYPE_SOUND|Plik dźwiękowy.|
|GOPHER_TYPE_HTML|Dokument HTML.|
|GOPHER_TYPE_PDF|Plik PDF.|
|GOPHER_TYPE_CALENDAR|Plik kalendarza.|
|GOPHER_TYPE_INLINE|Plik wbudowany.|
|GOPHER_TYPE_UNKNOWN|Typ towaru jest nieznany.|
|GOPHER_TYPE_ASK|Element Ask+.|
|GOPHER_TYPE_GOPHER_PLUS|Element Gopher+.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::operator LPCTSTR

Ten użyteczny operator rzutowania zapewnia wydajną metodę dostępu do `CGopherLocator` ciągu C zakończonego wartością null zawartego w obiekcie.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Żadne znaki nie są kopiowane; zwracany jest tylko wskaźnik.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)
