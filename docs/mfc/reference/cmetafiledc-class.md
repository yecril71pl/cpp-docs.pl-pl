---
title: CMetaFileDC Class
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 61e8442c085a5be0a7266409daf973bf63f52a7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505505"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC Class

Implementuje metaplik systemu Windows, który zawiera sekwencję poleceń interfejsu urządzenia graficznego (GDI), które można odtworzyć, aby utworzyć żądany obraz lub tekst.

## <a name="syntax"></a>Składnia

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Konstruuje `CMetaFileDC` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|Zamyka kontekst urządzenia i tworzy uchwyt metapliku.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Zamyka kontekst urządzenia z ulepszonymi metaplikami i tworzy dojście ulepszonego metapliku.|
|[CMetaFileDC:: Create](#create)|Tworzy kontekst urządzenia metaplików systemu Windows i dołącza go do `CMetaFileDC` obiektu.|
|[CMetaFileDC:: isenhanced](#createenhanced)|Tworzy kontekst urządzenia metaplik dla metapliku ulepszonego formatu.|

## <a name="remarks"></a>Uwagi

Aby zaimplementować metaplik systemu Windows, najpierw Utwórz `CMetaFileDC` obiekt. Wywołaj `CMetaFileDC` konstruktora, a następnie wywołaj funkcję Create member, która tworzy kontekst urządzenia metaplików systemu Windows i dołącza go do obiektu. [](#create) `CMetaFileDC`

Następnie Wyślij `CMetaFileDC` do obiektu sekwencję poleceń GDI przechwytywania, które mają być odtwarzane. Można używać tylko tych poleceń GDI, które tworzą dane `MoveTo` wyjściowe `LineTo`, takie jak i.

Po wysłaniu wymaganych poleceń do metapliku Wywołaj `Close` funkcję członkowską, która zamknie konteksty urządzenia metapliku i zwróci uchwyt metapliku. Następnie usuń `CMetaFileDC` obiekt.

Przegranie [::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) może następnie użyć uchwytu metapliku do wielokrotnego odtwarzania metapliku. Metaplik może być również manipulowany przez funkcje systemu Windows, takie jak [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), które kopiuje metaplik na dysk.

Gdy metaplik nie jest już potrzebne, usuń go z pamięci za pomocą funkcji [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) systemu Windows.

Można również zaimplementować `CMetaFileDC` obiekt, aby mógł obsługiwać zarówno wywołania wyjściowe, jak i wywołania GDI atrybutów, takich jak `GetTextExtent`. Taki metaplik jest bardziej elastyczny i można łatwiej ponownie wykorzystać ogólny kod GDI, który często składa się z mieszania wywołań wyjściowych i atrybutów. Klasa dziedziczy dwa `m_hDC` konteksty urządzeń i `m_hAttribDC`, z danych przechwytywania. `CMetaFileDC` Kontekst urządzenia obsługuje wszystkie wywołania `m_hAttribDC` wyjściowe GDI przechwytywania, a kontekst urządzenia obsługuje wszystkie wywołania atrybutów GDI przechwytywania. [](../../mfc/reference/cdc-class.md) `m_hDC` Zwykle te dwa konteksty urządzenia odwołują się do tego samego urządzenia. W przypadku `CMetaFileDC`, atrybut DC ma domyślnie wartość null.

Utwórz drugi kontekst urządzenia, który wskazuje na ekran, drukarkę lub urządzenie inne niż metaplik, a następnie Wywołaj `SetAttribDC` funkcję członkowską, aby skojarzyć nowy kontekst urządzenia z. `m_hAttribDC` Wywołania GDI dla informacji będą teraz kierowane do nowego `m_hAttribDC`. Wyjściowe wywołania GDI przechodzą do `m_hDC`, który reprezentuje metaplik.

Aby uzyskać więcej informacji `CMetaFileDC`na temat, zobacz [konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="close"></a>CMetaFileDC:: Close

Zamyka kontekst urządzenia metapliku i tworzy uchwyt metapliku systemu Windows, który może być używany do odtwarzania metapliku przy użyciu funkcji " [:P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) ".

```
HMETAFILE Close();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy HMETAFILE, jeśli funkcja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Uchwyt metapliku systemu Windows może być również używany do manipulowania metaplikiem z funkcjami systemu Windows, takimi jak [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Usuń metaplik po użyciu, wywołując funkcję [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) systemu Windows.

##  <a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced

Zamyka kontekst urządzenia z ulepszonym metaplikiem i zwraca dojście, które identyfikuje metaplik w formacie rozszerzonym.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do ulepszonego metapliku, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aplikacja może używać dojścia ulepszonego metapliku zwróconego przez tę funkcję do wykonywania następujących zadań:

- Wyświetlanie obrazu przechowywanego w rozszerzonym formacie metapliku

- Utwórz kopie rozszerzonego metapliku

- Wyliczanie, edytowanie lub kopiowanie pojedynczych rekordów w rozszerzonym formacie metapliku

- Pobierz opcjonalny opis zawartości metapliku z nagłówka rozszerzonego metapliku

- Pobierz kopię nagłówka rozszerzonego metapliku

- Pobierz binarną kopię rozszerzonego metapliku

- Wylicz kolory w opcjonalnej palecie

- Konwertowanie metapliku rozszerzonego formatu na metaplik formatu Windows

Gdy aplikacja nie potrzebuje już ulepszonego uchwytu metapliku, powinna zwolnić dojście, wywołując funkcję Win32 `DeleteEnhMetaFile` .

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

`CMetaFileDC` Utwórz obiekt w dwóch krokach.

```
CMetaFileDC();
```

### <a name="remarks"></a>Uwagi

Najpierw należy wywołać `CMetaFileDC`metodę, a `Create`następnie wywołać, która tworzy kontekst urządzenia metaplików systemu Windows i `CMetaFileDC` dołącza go do obiektu.

##  <a name="create"></a>CMetaFileDC:: Create

`CMetaFileDC` Utwórz obiekt w dwóch krokach.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFilename*<br/>
Wskazuje ciąg znaków zakończony znakiem null. Określa nazwę pliku metapliku do utworzenia. Jeśli *lpszFileName* ma wartość null, tworzony jest nowy metaplik w pamięci.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Najpierw Wywołaj konstruktora `CMetaFileDC`, a następnie Wywołaj `Create`, który tworzy kontekst urządzenia metaplików systemu Windows i `CMetaFileDC` dołącza go do obiektu.

##  <a name="createenhanced"></a>CMetaFileDC:: isenhanced

Tworzy kontekst urządzenia dla metapliku ulepszonego formatu.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parametry

*pDCRef*<br/>
Identyfikuje urządzenie odniesienia dla rozszerzonego metapliku.

*lpszFileName*<br/>
Wskazuje ciąg znaków zakończony znakiem null. Określa nazwę pliku dla rozszerzonego metapliku, który ma zostać utworzony. Jeśli ten parametr ma wartość null, rozszerzony metaplik jest oparty na pamięci i jego zawartość utracona, gdy obiekt jest niszczony lub `DeleteEnhMetaFile` gdy wywoływana jest funkcja Win32.

*lpBounds*<br/>
Wskazuje na strukturę danych [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , który określa wymiary w jednostkach HIMETRIC (w przyrostach .01-milimetrowych) obrazu, który ma być przechowywany w rozszerzonym metapliku.

*lpszDescription*<br/>
Wskazuje ciąg zakończony zerem, który określa nazwę aplikacji, która utworzyła obraz, a także tytuł obrazu.

### <a name="return-value"></a>Wartość zwracana

Dojście kontekstu urządzenia dla rozszerzonego metapliku, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten kontroler domeny może służyć do przechowywania obrazu niezależnego od urządzenia.

System Windows używa urządzenia referencyjnego identyfikowanego przez parametr *pDCRef* do rejestrowania rozdzielczości i jednostek urządzenia, na których zdjęcie pojawiło się pierwotnie. Jeśli parametr *pDCRef* ma wartość null, używa bieżącego urządzenia wyświetlającego jako odwołanie.

Lewe i górne składowe `RECT` struktury danych wskazywane przez parametr *lpBounds* muszą być mniejsze niż prawa i dolny element członkowski. Na obrazie znajdują się punkty wzdłuż brzegów prostokąta. Jeśli *lpBounds* ma wartość null, interfejs urządzenia graficznego (GDI) oblicza wymiary najmniejszego prostokąta, który może obejmować obraz rysowany przez aplikację. Należy podać parametr *lpBounds* , jeśli jest to możliwe.

Ciąg wskazany przez parametr *lpszDescription* musi zawierać znak null między nazwą aplikacji a nazwą obrazu i musi kończyć się dwoma znakami null, na przykład "XYZ Graphics Editor\0Bald Eagle\0\0," gdzie \ 0 reprezentuje znak o wartości null. Jeśli *lpszDescription* ma wartość null, nie ma odpowiadającego mu wpisu w nagłówku rozszerzonego metapliku.

Aplikacje używają kontrolera domeny utworzonego przez tę funkcję do przechowywania obrazu grafiki w rozszerzonym formacie metapliku. Dojście identyfikujące ten kontroler domeny może zostać przesłane do dowolnej funkcji GDI.

Gdy aplikacja przechowuje obraz w rozszerzonym metapliku, może wyświetlić obraz na dowolnym urządzeniu wyjściowym, wywołując `CDC::PlayMetaFile` funkcję. Podczas wyświetlania obrazu system Windows używa prostokąta wskazywanego przez parametr *lpBounds* oraz dane rozdzielczości z urządzenia odniesienia, aby pomieścić i skalować obraz. Kontekst urządzenia zwrócony przez tę funkcję zawiera te same atrybuty domyślne skojarzone z dowolnym nowym kontrolerem domeny.

Aplikacje muszą używać funkcji Win32 `GetWinMetaFileBits` do konwersji rozszerzonego metapliku na starszy format metapliku systemu Windows.

Nazwa pliku dla rozszerzonego metapliku powinna używać. Rozszerzenie EMF.

## <a name="see-also"></a>Zobacz także

[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
