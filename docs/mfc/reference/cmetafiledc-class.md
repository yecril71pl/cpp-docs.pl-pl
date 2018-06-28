---
title: Cmetafiledc — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eaec2b7951b0655a8a47106374c7527dad27bd20
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039540"
---
# <a name="cmetafiledc-class"></a>Cmetafiledc — klasa
Implementuje metaplik systemu Windows, który zawiera sekwencję grafiki urządzenia (GDI) interfejsu poleceń, które odtwarzasz można utworzyć odpowiedni obraz lub tekst.  
  
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
|[CMetaFileDC::Create](#create)|Tworzy kontekst urządzenia Windows metafile i dołącza go do `CMetaFileDC` obiektu.|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Tworzy metaplik kontekstu urządzenia dla formatu rozszerzony metaplik.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zaimplementować metaplik systemu Windows, należy najpierw utworzyć `CMetaFileDC` obiektu. Wywołanie `CMetaFileDC` konstruktora, następnie wywołaj [Utwórz](#create) funkcji członkowskiej, która tworzy kontekstu urządzenia Windows metafile i dołącza go do `CMetaFileDC` obiektu.  
  
 Następnie wysłać `CMetaFileDC` obiekt sekwencji `CDC` GDI polecenia przeznaczonych dla niego powtarzania. Tylko tych poleceń GDI tworzące dane wyjściowe, takich jak `MoveTo` i `LineTo`, mogą być używane.  
  
 Po żądanych poleceń zostało wysłane do metaplik, wywołać `Close` funkcji członkowskiej, który zamyka metaplik kontekstach urządzenia i zwraca uchwyt metaplik. Następnie usuwa `CMetaFileDC` obiektu.  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) dojście metaplik można następnie użyć do odtwarzanie metaplik. Metaplik może również używać funkcji systemu Windows takich jak [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480), który kopiuje metaplik na dysku.  
  
 Metaplik jest już potrzebne, usuń go z pamięci z [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) funkcji systemu Windows.  
  
 Można też wdrożyć `CMetaFileDC` obiekt, tak aby może obsługiwać zarówno dane wyjściowe wywołań i atrybutu wywołań interfejsu GDI, takich jak `GetTextExtent`. Takie metaplik jest bardziej elastyczna i więcej łatwo korzystać ponownie ogólne GDI, który często składa się z kombinacji wywołań wyjściowych i atrybut. `CMetaFileDC` Klasa dziedziczy dwóch kontekstów urządzenia, `m_hDC` i `m_hAttribDC`, z `CDC`. `m_hDC` Kontekstu urządzenia obsługuje wszystkie [CDC](../../mfc/reference/cdc-class.md) GDI output wywołań i `m_hAttribDC` kontekstu urządzenia obsługuje wszystkie `CDC` GDI atrybut wywołania. Zwykle te konteksty urządzenia dwóch odwoływać się do tego samego urządzenia. W przypadku liczby `CMetaFileDC`, atrybut kontrolera domeny jest ustawiony na **NULL** domyślnie.  
  
 Utworzyć drugi kontekst urządzenia, który wskazuje na ekranie, drukarki lub urządzenia innego niż metaplików wywoływać `SetAttribDC` funkcji członkowskiej, aby skojarzyć nowy kontekst urządzenia z `m_hAttribDC`. Wywołania interfejsu GDI informacje będą teraz kierowane do nowego `m_hAttribDC`. Dane wyjściowe GDI wywołania nastąpi przejście do `m_hDC`, który reprezentuje metaplik.  
  
 Aby uzyskać więcej informacji na temat `CMetaFileDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="close"></a>  CMetaFileDC::Close  
 Zamyka metaplik kontekstu urządzenia i tworzy dojście metaplik systemu Windows, który może służyć do odtwarzania metaplik przy użyciu [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) funkcję elementu członkowskiego.  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Prawidłowy **HMETAFILE** przypadku powodzenia; w przeciwnym razie funkcja **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Dojście metaplik systemu Windows mogą służyć do manipulowania metaplik z funkcjami systemu Windows, takich jak [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480).  
  
 Usuń metaplik po użyciu przez wywołanie systemu Windows [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) funkcji.  
  
##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced  
 Zamyka rozszerzonych metaplików kontekstu urządzenia i zwraca uchwyt identyfikuje format rozszerzony metaplik.  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt rozszerzony metaplik, w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja może użyć dojście rozszerzonych metaplików zwracane przez tę funkcję można wykonywać następujące zadania:  
  
-   Wyświetl obraz przechowywany w rozszerzony metaplik  
  
-   Utwórz kopie rozszerzony metaplik  
  
-   Wyliczanie, edytować lub skopiuj poszczególne rekordy rozszerzony metaplik  
  
-   Pobierz opcjonalny opis zawartości metaplik z nagłówka rozszerzonych metaplików  
  
-   Pobierz kopię nagłówka rozszerzonych metaplików  
  
-   Pobrać kopię binarne rozszerzony metaplik  
  
-   Wyliczanie kolorów w palecie opcjonalne  
  
-   Konwertuj metaplik rozszerzony format w metaplik formatu Windows  
  
 Gdy aplikacja nie będzie już potrzebował dojście rozszerzony metaplik, należy zwolnić dojścia wywołując Win32 **DeleteEnhMetaFile** funkcji.  
  
##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC  
 Utworzyć `CMetaFileDC` obiektu w dwóch krokach.  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>Uwagi  
 Najpierw należy wywołać `CMetaFileDC`, następnie wywołaj **Utwórz**, która tworzy kontekst urządzenia Windows metafile i dołącza go do `CMetaFileDC` obiektu.  
  
##  <a name="create"></a>  CMetaFileDC::Create  
 Utworzyć `CMetaFileDC` obiektu w dwóch krokach.  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFilename*  
 Wskazuje ciąg znaków zakończony znakiem null. Określa nazwę pliku metaplik do utworzenia. Jeśli *lpszFilename* jest **NULL**, jest tworzony nowy metaplik w pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po pierwsze wywołanie konstruktora `CMetaFileDC`, następnie wywołaj **Utwórz**, która tworzy kontekst urządzenia Windows metafile i dołącza go do `CMetaFileDC` obiektu.  
  
##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced  
 Tworzy kontekstu urządzenia dla formatu rozszerzony metaplik.  
  
```  
BOOL CreateEnhanced(
    CDC* pDCRef,  
    LPCTSTR lpszFileName,  
    LPCRECT lpBounds,  
    LPCTSTR lpszDescription);
```  
  
### <a name="parameters"></a>Parametry  
 *pDCRef*  
 Identyfikuje urządzenie odwołanie na potrzeby rozszerzony metaplik.  
  
 *lpszFileName*  
 Wskazuje ciąg znaków zakończony znakiem null. Określa nazwę pliku rozszerzony metaplik ma zostać utworzony. Jeśli ten parametr ma **NULL**, rozszerzony metaplik jest pamięci na podstawie i jego zawartość utraty, gdy obiekt zostanie zniszczony lub Win32 **DeleteEnhMetaFile** funkcja jest wywoływana.  
  
 *lpBounds*  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury danych lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który określa wymiary w **HIMETRIC** jednostki (w przyrostach.01 milimetra) obraz ma być przechowywany w rozszerzony metaplik.  
  
 *lpszDescription*  
 Wskazuje ciąg zakończony zerem, który określa nazwę aplikacji, która utworzyła obraz, tytuł obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt kontekstu urządzenia rozszerzony metaplik, w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten kontroler domeny może służyć do przechowywania obrazu niezależnych od urządzenia.  
  
 System Windows używa urządzenia odwołanie określone przez *pDCRef* parametr, aby zarejestrować rozdzielczość i jednostki urządzenia, na którym pierwotnie pojawił się obraz. Jeśli *pDCRef* parametr jest **NULL**, używa bieżące urządzenie wyświetlające odwołania.  
  
 Po lewej stronie i największe członków `RECT` struktury danych wskazywanego przez *lpBounds* parametru musi być mniejsza niż elementy w prawo i w dół, odpowiednio. Punkty wzdłuż krawędzi prostokąta znajdują się na obrazie. Jeśli *lpBounds* jest **NULL**, graficzny interfejs urządzenia (GDI) oblicza wymiary najmniejszego prostokąta, który można umieścić obraz rysowane przez aplikację. *LpBounds* podany parametr, jeśli jest to możliwe.  
  
 Ciąg wskazywana przez *lpszDescription* parametr musi zawierać znak null między nazwę aplikacji i nazwę obrazu i musi kończyć się znakami null — na przykład "XYZ grafiki Editor\0Bald Eagle\0\0, "gdzie \0 reprezentuje znak null. Jeśli *lpszDescription* jest **NULL**, Brak odpowiedniego wpisu w nagłówku rozszerzony metaplik.  
  
 Aplikacje do przechowywania obrazu grafiki w rozszerzony metaplik używają DC utworzony przez tę funkcję. Dojście identyfikujący ten kontroler domeny mogą być przekazywane do dowolnej funkcji GDI.  
  
 Po aplikacja przechowuje obrazu w rozszerzony metaplik, będzie możliwe wyświetlenie obraz na dowolnym urządzeniu danych wyjściowych przez wywołanie metody `CDC::PlayMetaFile` funkcji. Podczas wyświetlania obrazu, system Windows używa prostokąt wskazywana przez *lpBounds* parametrów i danych rozwiązania z urządzenia odwołania do umieszczenia i Skaluj obraz. Kontekst urządzenia zwracane przez tę funkcję zawiera te same atrybuty domyślne skojarzone z dowolnego nowego kontrolera domeny.  
  
 Aplikacje muszą używać środowiska Win32 **GetWinMetaFileBits** funkcji konwersji do formatu Windows metafile starsze rozszerzony metaplik.  
  
 Należy użyć nazwy pliku dla rozszerzony metaplik. Rozszerzenie EMF.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



