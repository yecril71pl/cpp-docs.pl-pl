---
title: Klasa CGopherFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 083ed824ce8586295e398d32ed14e17f8d334358
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080952"
---
# <a name="cgopherfile-class"></a>Cgopherfile — klasa

Oferuje funkcje w celu odnalezienia i odczytania plików na serwerze gophera.

> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementów członkowskich są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działały na starszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|Konstruuje `CGopherFile` obiektu.|

## <a name="remarks"></a>Uwagi

Usługa gopher nie zezwala użytkownikom można zapisać danych do pliku gopher, ponieważ ta usługa działa głównie jako interfejs do znajdowania informacji. `CGopherFile` Elementów członkowskich `Write`, `WriteString`, i `Flush` nie są zaimplementowane dla `CGopherFile`. Wywoływanie tych funkcji na `CGopherFile` obiektu i zwraca [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby dowiedzieć się więcej o tym, jak `CGopherFile` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile

Ta funkcja członkowska jest wywoływana, aby skonstruować `CGopherFile` obiektu.

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

*hFile —*<br/>
Dojście do pliku HINTERNET.

*refLocator*<br/>
Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.

*pConnection*<br/>
Wskaźnik do [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) obiektu.

*hSession*<br/>
Dojście do bieżącej sesji Internet.

*pstrLocator*<br/>
Wskaźnik do ciągu, używana do lokalizowania serwera gopher. Zobacz [sesje Gopher](cgopherlocator-class.md) Aby uzyskać więcej informacji na temat lokalizatorów gopher.

*dwLocLen*<br/>
DWORD zawierającą liczbę bajtów w *pstrLocator*.

*dwContext*<br/>
Wskaźnik na identyfikator kontekstu otwierany plik.

### <a name="remarks"></a>Uwagi

Potrzebujesz `CGopherFile` obiektu do odczytu z pliku podczas sesji Internet gopher.

Nigdy nie twórz `CGopherFile` obiektu bezpośrednio. Zamiast tego należy wywołać [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) można otworzyć pliku na serwerze gophera.

## <a name="see-also"></a>Zobacz też

[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
