---
title: Klasa CMetaFileDC
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
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369948"
---
# <a name="cmetafiledc-class"></a>Klasa CMetaFileDC

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
|[CMetaFileDC::Zamknij](#close)|Zamyka kontekst urządzenia i tworzy uchwyt metapliku.|
|[CMetaFileDC::ZamknijEnhanced](#closeenhanced)|Zamyka rozszerzony kontekst urządzenia metaplikowego i tworzy uchwyt rozszerzonego metapliku.|
|[CMetaFileDC::Utwórz](#create)|Tworzy kontekst urządzenia metaplik systemu Windows `CMetaFileDC` i dołącza go do obiektu.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Tworzy kontekst urządzenia metapliku dla rozszerzonego formatu metapliku.|

## <a name="remarks"></a>Uwagi

Aby zaimplementować metaplik `CMetaFileDC` systemu Windows, należy najpierw utworzyć obiekt. Wywołaj `CMetaFileDC` konstruktora, a następnie [wywołaj](#create) funkcję Create member, która tworzy kontekst `CMetaFileDC` urządzenia metapliku systemu Windows i dołącza go do obiektu.

Następnie wyślij `CMetaFileDC` obiekt sekwencji CDC GDI poleceń, które zamierzasz go odtworzyć. Można używać tylko tych poleceń GDI, które tworzą dane wyjściowe, takie jak `MoveTo` i `LineTo`, mogą być używane.

Po wysłaniu żądanych poleceń do metapliku należy wywołać funkcję `Close` elementu członkowskiego, która zamyka konteksty urządzeń metaplikowych i zwraca uchwyt metapliku. Następnie zutylizuj `CMetaFileDC` obiekt.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) może następnie używać uchwytu metapliku do wielokrotnego odtwarzania metapliku. Metaplik może być również manipulowany przez funkcje systemu Windows, takie jak [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), który kopiuje metaplik na dysk.

Gdy metaplik nie jest już potrzebny, usuń go z pamięci za pomocą funkcji [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows.

Można również zaimplementować `CMetaFileDC` obiekt, dzięki czemu może obsługiwać zarówno `GetTextExtent`wywołania wyjściowe, jak i wywołania GDI, takie jak . Taki metaplik jest bardziej elastyczny i można łatwiej ponownie użyć ogólnego kodu GDI, który często składa się z kombinacji wywołań wyjściowych i atrybutów. Klasa `CMetaFileDC` dziedziczy dwa konteksty `m_hDC` `m_hAttribDC`urządzenia i , z CDC. Kontekst `m_hDC` urządzenia obsługuje wszystkie wywołania wyjściowe `m_hAttribDC` GDI [CDC,](../../mfc/reference/cdc-class.md) a kontekst urządzenia obsługuje wszystkie wywołania atrybutów CDC GDI. Zwykle te dwa konteksty urządzenia odnoszą się do tego samego urządzenia. W przypadku `CMetaFileDC`, atrybut DC jest domyślnie ustawiona na wartość NULL.

Utwórz drugi kontekst urządzenia, który wskazuje na ekranie, drukarce lub urządzeniu `SetAttribDC` inne niż metaplik, `m_hAttribDC`a następnie zadzwoń do funkcji członkowskiej, aby skojarzyć nowy kontekst urządzenia z programem . Wezwania GDI do uzyskania informacji będą `m_hAttribDC`teraz kierowane do nowego . Wyjściowe wywołania GDI zostaną `m_hDC`donikowe , który reprezentuje metaplik.

Aby uzyskać `CMetaFileDC`więcej informacji na temat , zobacz [Konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC::Zamknij

Zamyka kontekst urządzenia metaplik i tworzy uchwyt metapliku systemu Windows, który może być używany do odtwarzania metapliku przy użyciu funkcji członkowskiej [CDC::PlayMetaFile.](../../mfc/reference/cdc-class.md#playmetafile)

```
HMETAFILE Close();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowa hmetafile, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Uchwyt metapliku systemu Windows może być również używany do manipulowania metaplikem za pomocą funkcji systemu Windows, takich jak [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Usuń metaplik po użyciu, wywołując funkcję [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) systemu Windows.

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC::ZamknijEnhanced

Zamyka kontekst urządzenia z rozszerzonym metaplikem i zwraca dojście identyfikujące metaplik w formacie rozszerzonym.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt ulepszonego metapliku, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Aplikacja może użyć uchwytu rozszerzonego metapliku zwróconego przez tę funkcję do wykonywania następujących zadań:

- Wyświetlanie obrazu zapisanego w rozszerzonym metapliku

- Tworzenie kopii rozszerzonego metapliku

- Wyliczaj, edytuj lub kopiuj poszczególne rekordy w rozszerzonym metapliku

- Pobieranie opcjonalnego opisu zawartości metapliku z nagłówka rozszerzonego metapliku

- Pobieranie kopii nagłówka rozszerzonego metapliku

- Pobieranie binarnej kopii rozszerzonego metapliku

- Wyliczaj kolory w opcjonalnej palecie

- Konwertowanie metapliku w formacie rozszerzonym na metaplik w formacie Windows

Gdy aplikacja nie potrzebuje już uchwytu metapliku rozszerzonego, należy zwolnić `DeleteEnhMetaFile` dojście, wywołując funkcję Win32.

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC

Konstruuj `CMetaFileDC` obiekt w dwóch krokach.

```
CMetaFileDC();
```

### <a name="remarks"></a>Uwagi

Najpierw wywołaj `CMetaFileDC`, `Create`a następnie wywołaj , który tworzy kontekst `CMetaFileDC` urządzenia metaplik systemu Windows i dołącza go do obiektu.

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC::Utwórz

Konstruuj `CMetaFileDC` obiekt w dwóch krokach.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFilename*<br/>
Wskazuje ciąg znaków zakończony z wartością null. Określa nazwę pliku metapliku do utworzenia. Jeśli *lpszFilename* ma wartość NULL, tworzony jest nowy metaplik w pamięci.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Najpierw wywołaj konstruktora, `CMetaFileDC`a następnie wywołaj `Create`, który tworzy kontekst `CMetaFileDC` urządzenia metapliku systemu Windows i dołącza go do obiektu.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC::CreateEnhanced

Tworzy kontekst urządzenia dla metapliku w formacie rozszerzonym.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parametry

*pDCRef*<br/>
Identyfikuje urządzenie referencyjne dla ulepszonego metapliku.

*lpszFileName*<br/>
Wskazuje ciąg znaków zakończony z wartością null. Określa nazwę pliku rozszerzonego metapliku, który ma zostać utworzony. Jeśli ten parametr ma wartość NULL, rozszerzony metaplik jest oparty na pamięci, a `DeleteEnhMetaFile` jego zawartość zostanie utracona, gdy obiekt zostanie zniszczony lub gdy wywoływana jest funkcja Win32.

*lpBounds (Obfity)*<br/>
Wskazuje strukturę danych [RECT](/windows/win32/api/windef/ns-windef-rect) lub obiekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) który określa wymiary w jednostkach HIMETRIC (w przyrostach 0,01 milimetra) obrazu, który ma być przechowywany w rozszerzonym metapliku.

*lpszDescription*<br/>
Wskazuje ciąg zakończony zerem, który określa nazwę aplikacji, która utworzyła obraz, a także tytuł obrazu.

### <a name="return-value"></a>Wartość zwracana

Uchwyt kontekstu urządzenia dla rozszerzonego metapliku, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten kontroler domeny może służyć do przechowywania obrazu niezależnego od urządzenia.

System Windows używa urządzenia referencyjnego identyfikowanego przez parametr *pDCRef* do rejestrowania rozdzielczości i jednostek urządzenia, na którym pierwotnie pojawił się obraz. Jeśli *parametrem pDCRef* jest NULL, używa bieżącego urządzenia wyświetlającego w celach informacyjnych.

Lewe i górne `RECT` elementy członkowskie struktury danych wskazywali przez *parametr lpBounds* muszą być odpowiednio mniejsze niż prawe i dolne elementy członkowskie. Punkty wzdłuż krawędzi prostokąta są uwzględniane na rysunku. Jeśli *lpBounds* ma wartość NULL, interfejs urządzenia graficznego (GDI) oblicza wymiary najmniejszego prostokąta, który może ująć obraz rysowany przez aplikację. W miarę możliwości należy podać parametr *lpBounds.*

Ciąg wskazyny przez parametr *lpszDescription* musi zawierać znak null między nazwą aplikacji a nazwą obrazu i musi zakończyć się dwoma znakami null — na przykład "XYZ Graphics Editor\0Bald Eagle\0\0", gdzie \0 reprezentuje znak null. Jeśli *lpszDescription* ma wartość NULL, nie ma odpowiedniego wpisu w nagłówku enhanced-metafile.

Aplikacje używają kontrolera domeny utworzonego przez tę funkcję do przechowywania obrazu graficznego w rozszerzonym metapliku. Dojście identyfikujące ten kontroler domeny można przekazać do dowolnej funkcji GDI.

Po aplikacji przechowuje obraz w rozszerzonym metaplik, może wyświetlić obraz `CDC::PlayMetaFile` na dowolnym urządzeniu wyjściowym, wywołując funkcję. Podczas wyświetlania obrazu system Windows używa prostokąta wskazanego przez parametr *lpBounds* i danych rozdzielczości z urządzenia referencyjnego do położenia i skalowania obrazu. Kontekst urządzenia zwrócony przez tę funkcję zawiera te same atrybuty domyślne skojarzone z dowolnym nowym kontrolerem domeny.

Aplikacje muszą używać `GetWinMetaFileBits` funkcji Win32 do konwersji rozszerzonego metapliku na starszy format metapliku systemu Windows.

Nazwa pliku rozszerzonego metapliku powinna być używana przez plik . rozszerzenie EMF.

## <a name="see-also"></a>Zobacz też

[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
