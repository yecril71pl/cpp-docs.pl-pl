---
title: Klasa CGopherFile
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373692"
---
# <a name="cgopherfile-class"></a>Klasa CGopherFile

Zapewnia funkcje znajdowania i odczytywania plików na serwerze gopher.

> [!NOTE]
> Klasy `CGopherConnection`, `CGopherFile` `CGopherFileFind`, `CGopherLocator` i ich członkowie zostały przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą nadal działać na wcześniejszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|Konstruuje `CGopherFile` obiekt.|

## <a name="remarks"></a>Uwagi

Usługa gopher nie pozwala użytkownikom na zapisywanie danych do pliku gopher, ponieważ ta usługa działa głównie jako interfejs oparty na menu do znajdowania informacji. Funkcje `CGopherFile` `Write`członkowskie `WriteString`, `Flush` i nie `CGopherFile`są implementowane dla . Wywołując te funkcje w obiekcie, `CGopherFile` zwraca [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby dowiedzieć `CGopherFile` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Cstdiofile](../../mfc/reference/cstdiofile-class.md)

[Cinternetfile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopherFile::CGopherFile

Ta funkcja elementu członkowskiego `CGopherFile` jest wywoływana do konstruowania obiektu.

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>Parametry

*hFile (plik)*<br/>
Dojście do pliku HINTERNET.

*reflocator*<br/>
Odwołanie do [obiektu CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*pZkładanie*<br/>
Wskaźnik do [obiektu CGopherConnection.](../../mfc/reference/cgopherconnection-class.md)

*hSession (wysiew)*<br/>
Dojście do bieżącej sesji internetowej.

*lokalizator pstrLocator*<br/>
Wskaźnik do ciągu używanego do lokalizowania serwera gopher. Zobacz [Sesje gopher, aby](cgopherlocator-class.md) uzyskać więcej informacji na temat lokalizatorów gopher.

*dwLocLen (ł.*<br/>
A DWORD zawierający liczbę bajtów w *pstrLocator*.

*Dwcontext*<br/>
Wskaźnik do identyfikatora kontekstu otwieranego pliku.

### <a name="remarks"></a>Uwagi

Do odczytu `CGopherFile` z pliku podczas sesji internetowej gopher potrzebny jest obiekt.

Nigdy nie `CGopherFile` tworzysz obiektu bezpośrednio. Zamiast tego zadzwoń do [CGopherConnection::OpenFile,](../../mfc/reference/cgopherconnection-class.md#openfile) aby otworzyć plik na serwerze typu gopher.

## <a name="see-also"></a>Zobacz też

[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
