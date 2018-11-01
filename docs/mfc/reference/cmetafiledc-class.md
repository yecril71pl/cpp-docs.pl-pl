---
title: Cmetafiledc — klasa
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
ms.openlocfilehash: 343ab1a5d0c38ab0d17c609fbfc134b144502553
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471815"
---
# <a name="cmetafiledc-class"></a>Cmetafiledc — klasa

Implementuje metaplik Windows, który zawiera sekwencję poleceń interface (GDI) urządzenia grafiki, które można powtarzać tak, aby utworzyć żądany obraz lub tekst.

## <a name="syntax"></a>Składnia

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Konstruuje `CMetaFileDC` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|Zamyka kontekstu urządzenia i tworzy dojście metaplik.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Zamyka rozszerzonych metaplików kontekstu urządzenia i tworzy dojście rozszerzony metaplik.|
|[CMetaFileDC::Create](#create)|Tworzy kontekst urządzenia metaplików Windows i dołącza je do `CMetaFileDC` obiektu.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Tworzy metaplik kontekst urządzenia dla formatu rozszerzony metaplik.|

## <a name="remarks"></a>Uwagi

Aby zaimplementować metaplik Windows, należy najpierw utworzyć `CMetaFileDC` obiektu. Wywoływanie `CMetaFileDC` Konstruktor, następnie wywołać [Utwórz](#create) funkcji elementu członkowskiego, która tworzy kontekście urządzenia metaplików Windows i dołącza je do `CMetaFileDC` obiektu.

Następnie wyślij `CMetaFileDC` obiektu sekwencja poleceń GDI przechwytywania zmian danych, przeznaczonych dla niego do odtworzenia. Tylko tych poleceń interfejsu GDI, tworzące dane wyjściowe, takie jak `MoveTo` i `LineTo`, mogą być używane.

Po zostało wysłane żądanego polecenia, aby metaplik, wywołać `Close` funkcja elementu członkowskiego, który zamyka konteksty urządzenia metaplików i zwraca uchwyt metaplik. Następnie usuwa `CMetaFileDC` obiektu.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) można następnie użyć uchwytu metaplik powtarzanie odtwarzania metaplik. Metaplik może również być manipulowane przez Windows funkcje takie jak [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea), który kopiuje metaplik na dysku.

Gdy metaplik nie jest już potrzebny, usuń go z pamięci za pomocą [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) funkcji Windows.

Możesz również wdrożyć `CMetaFileDC` obiekt, tak aby może obsługiwać zarówno dane wyjściowe wywołania i atrybutu wywołania interfejsu GDI, takich jak `GetTextExtent`. Takie metaplik jest bardziej elastyczna i więcej z łatwością wykorzystać ogólne kodu interfejsu GDI, który często składa się z różnych połączeń w danych wyjściowych i atrybut. `CMetaFileDC` Klasa dziedziczy dwa konteksty urządzenia, `m_hDC` i `m_hAttribDC`, z przechwytywania zmian danych. `m_hDC` Kontekstu urządzenia obsługuje wszystkie [CDC](../../mfc/reference/cdc-class.md) GDI dane wyjściowe wywołania i `m_hAttribDC` kontekstu urządzenia obsługuje wszystkie wywołania atrybut GDI przechwytywania zmian danych. Zazwyczaj te konteksty urządzenia dwóch odnoszą się do tego samego urządzenia. W przypadku właściwości `CMetaFileDC`, atrybut kontroler domeny jest domyślnie null.

Utwórz drugi kontekstu urządzenia, który wskazuje na ekranie, drukarki lub urządzenia inne niż metaplik, następnie wywołać `SetAttribDC` funkcja elementu członkowskiego, aby skojarzyć nowy kontekst urządzenia za pomocą `m_hAttribDC`. Wywołania interfejsu GDI dla informacje będą teraz kierowane do nowego `m_hAttribDC`. Wywołania interfejsu GDI dane wyjściowe zostanie umieszczona na `m_hDC`, która reprezentuje metaplik.

Aby uzyskać więcej informacji na temat `CMetaFileDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[PRZECHWYTYWANIE ZMIAN DANYCH](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="close"></a>  CMetaFileDC::Close

Zamyka kontekście urządzenia metaplików i tworzy dojście metaplik Windows, który może służyć do odtwarzania metaplik przy użyciu [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) funkcja elementu członkowskiego.

```
HMETAFILE Close();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowa HMETAFILE, jeśli funkcja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Uchwyt metaplik Windows można także do manipulowania metaplik za pomocą funkcji Windows, takich jak [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea).

Usuń metaplik po użyciu wywołując Windows [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) funkcji.

##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced

Zamyka rozszerzonych metaplików kontekstu urządzenia i zwraca uchwyt, który identyfikuje format rozszerzony metaplik.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt rozszerzony metaplik, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aplikacja może użyć uchwytu rozszerzonych metaplików zwrócona przez tę funkcję do wykonania następujących zadań:

- Wyświetl zdjęcie na rozszerzony metaplik

- Tworzenie kopii rozszerzony metaplik

- Wyliczanie, edytować lub kopiowanie poszczególnych rekordów w rozszerzony metaplik

- Pobrać opcjonalny opis zawartości metaplik z nagłówkiem rozszerzonych metaplików

- Pobierz kopię nagłówka rozszerzonych metaplików

- Pobierz kopię binarne rozszerzony metaplik

- Wyliczanie kolorów w palecie opcjonalne

- Konwertuj format rozszerzony metaplik w metaplik formatu Windows

Gdy aplikacja nie musi już rozszerzony metaplik uchwytu, należy zwolnić dojścia poprzez wywołanie Win32 `DeleteEnhMetaFile` funkcji.

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

Konstruowania `CMetaFileDC` obiektu w dwóch krokach.

```
CMetaFileDC();
```

### <a name="remarks"></a>Uwagi

Po pierwsze wywołanie `CMetaFileDC`, następnie wywołać `Create`, który tworzy kontekście urządzenia metaplików Windows i dołącza go do `CMetaFileDC` obiektu.

##  <a name="create"></a>  CMetaFileDC::Create

Konstruowania `CMetaFileDC` obiektu w dwóch krokach.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFilename*<br/>
Wskazuje ciąg znaków zakończony znakiem null. Określa nazwę pliku metaplik do utworzenia. Jeśli *lpszFilename* ma wartość NULL, zostanie utworzony nowy metaplik w pamięci.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po pierwsze wywołanie konstruktora `CMetaFileDC`, następnie wywołać `Create`, który tworzy kontekście urządzenia metaplików Windows i dołącza go do `CMetaFileDC` obiektu.

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

Tworzy kontekst urządzenia dla formatu rozszerzony metaplik.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parametry

*pDCRef*<br/>
Identyfikuje urządzenie odwołanie rozszerzony metaplik.

*lpszFileName*<br/>
Wskazuje ciąg znaków zakończony znakiem null. Określa nazwę pliku dla rozszerzony metaplik ma zostać utworzony. Jeśli ten parametr ma wartość NULL, rozszerzony metaplik jest pamięci na podstawie i jego zawartość, utraty, gdy obiekt zostanie zniszczony lub Win32 `DeleteEnhMetaFile` funkcja jest wywoływana.

*lpBounds*<br/>
Wskazuje [Prostokąt](../../mfc/reference/rect-structure1.md) struktury danych lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który określa wymiarów w jednostkach HIMETRIC (wielokrotność.01 milimetra) obraz ma być przechowywany w rozszerzony metaplik.

*lpszDescription*<br/>
Wskazuje ciąg zakończony zerem, określający nazwę aplikacji, która utworzyła obraz, a także tytuł obrazu.

### <a name="return-value"></a>Wartość zwracana

Uchwyt kontekstu urządzenia rozszerzony metaplik, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten kontroler domeny może służyć do przechowywania obrazu niezależnych od urządzenia.

Windows używa odwołania do urządzenia identyfikowane przez *pDCRef* parametru, aby zarejestrować rozdzielczość i jednostki urządzenia, na którym pierwotnie pojawiły się obraz. Jeśli *pDCRef* parametr ma wartość NULL, używa bieżące urządzenie wyświetlające dla odwołania.

Lewym i górnym członkowie `RECT` struktury danych, wskazywana przez *lpBounds* parametru musi być mniejszy niż elementy po prawej stronie i u dołu, odpowiednio. Na ilustracji znajdują się punkty wzdłuż krawędzi prostokąta. Jeśli *lpBounds* ma wartość NULL, graficzny interfejs urządzenia (GDI) oblicza wymiary najmniejszy prostokąt, który może być częścią obraz rysowane przez aplikację. *LpBounds* parametr powinien być dostarczony, jeśli jest to możliwe.

Ciąg wskazywany przez *lpszDescription* parametr musi zawierać znak null między nazwę aplikacji i obraz, nazwa i musi kończyć się znakami null — na przykład "XYZ grafiki Editor\0Bald Eagle\0\0, "gdzie \0 reprezentuje znak null. Jeśli *lpszDescription* ma wartość NULL, Brak odpowiedniego wpisu w nagłówku rozszerzony metaplik.

Aplikacje używają kontrolera domeny, utworzone przez tę funkcję do przechowywania obrazów graficznych w rozszerzony metaplik. Uchwyt identyfikujący ten kontroler domeny może być przekazywany do żadnej funkcji interfejsu GDI.

Po aplikacja przechowuje obrazu w rozszerzony metaplik, obraz umożliwia wyświetlanie na dowolnym urządzeniu danych wyjściowych przez wywołanie metody `CDC::PlayMetaFile` funkcji. Podczas wyświetlania obrazu, Windows używa prostokąt wskazywany przez *lpBounds* parametrów i danych rozwiązania z odwołania do urządzenia do umieszczenia i Skaluj obraz. Kontekst urządzenia zwrócona przez tę funkcję zawiera takie same atrybuty domyślne skojarzone z dowolnego nowego kontrolera domeny.

Aplikacje muszą używać Win32 `GetWinMetaFileBits` funkcję, aby skonwertować rozszerzony metaplik do starszego formatu Windows w metaplik.

Należy użyć nazwy pliku dla rozszerzony metaplik. Rozszerzenie EMF.

## <a name="see-also"></a>Zobacz też

[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

