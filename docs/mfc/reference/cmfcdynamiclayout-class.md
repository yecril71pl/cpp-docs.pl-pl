---
title: Klasa CMFCDynamicLayout | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
dev_langs: C++
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 29b161d889aefc55e818a16233212a55bdcb45de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcdynamiclayout-class"></a>Klasa CMFCDynamicLayout
Określa, jak przenieść i zmiany rozmiaru, ponieważ użytkownik zmienia rozmiar okna kontrolki w oknie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|Konstruuje `CMFCDynamicLayout` obiektu.|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDynamicLayout::AddItem](#additem)|Dodaje okno podrzędne, zwykle formantu, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.|  
|[CMFCDynamicLayout::Adjust](#adjust)|Dodaje okno podrzędne, zwykle formantu, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.|  
|[CMFCDynamicLayout::Create](#create)|Przechowuje i weryfikuje okno hosta.|  
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Zwraca wskaźnik do okna hosta.|  
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Zwraca rozmiar okna, poniżej którego układ nie jest dostosowywany.|  
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Pobiera prostokąt dla bieżącego obszaru klienckiego okna.|  
|[CMFCDynamicLayout::HasItem](#hasitem)|Sprawdza, czy formant podrzędny został dodany do układ dynamiczny.|  
|[CMFCDynamicLayout::IsEmpty](#isempty)|Sprawdza, czy układ dynamiczny ma nie okien podrzędnych dodane.|  
|[CMFCDynamicLayout::LoadResource](#loadresource)|Odczytuje układ dynamiczny z zasobów AFX_DIALOG_LAYOUT, a następnie stosuje układ okna hosta.|  
|statyczne [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|  
|statyczne [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|  
|statyczne [CMFCDynamicLayout::MoveNone](#movenone)|Pobiera [MoveSettings](#movesettings_structure) wartość, która reprezentuje nie ruchu pionowych lub poziomych formantu podrzędnego.|  
|statyczne [CMFCDynamicLayout::MoveVertical](#movevertical)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna obsługi.|  
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Ustawia rozmiar okna, poniżej którego układ nie jest dostosowywany.|  
|statyczne [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|  
|statyczne [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|  
|statyczne [CMFCDynamicLayout::SizeNone](#sizenone)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która reprezentuje nie uległ zmianie rozmiar kontrolki podrzędnej.|  
|statyczne [CMFCDynamicLayout::SizeVertical](#sizevertical)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej pionie zmieni się rozmiar, gdy użytkownik zmienia rozmiar okna obsługi.|  
  
## <a name="nested-types"></a>Zagnieżdżone typy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Struktura CMFCDynamicLayout::MoveSettings](#movesettings_structure)|Hermetyzuje przenoszenia danych dla formantów dynamicznych układu.|  
|[Cmfcdynamiclayout::sizesettings — struktura](#sizesettings_structure)|Hermetyzuje dane zmiany rozmiaru formantów w układzie dynamicznych.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxlayout.h  
  
##  <a name="additem"></a>CMFCDynamicLayout::AddItem  
 Dodaje okno podrzędne, zwykle formantu, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.  
  
```  
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

 
BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```  
  
### <a name="parameters"></a>Parametry  
 `hwnd`  
 Dojście do okna, aby dodać.  
  
 `nID`  
 Identyfikator formantu podrzędnego do dodania.  
  
 `moveSettings`  
 Struktura, która opisuje, jak kontrolka powinna zostać przeniesiona wraz ze zmianą rozmiaru okna.  
  
 `sizeSettings`  
 Struktura, która opisuje, jak powinny być zmieniony rozmiar formantu jako zmiany rozmiaru okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli element został dodany pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Położenie i rozmiar kontrolki podrzędnej jest zmienić dynamicznie, po zmianie rozmiaru okna hostowania.  
  
##  <a name="adjust"></a>CMFCDynamicLayout::Adjust  
 Dodaje okno podrzędne, zwykle formantu, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.  
  
```  
void Adjust();
```  
  
### <a name="remarks"></a>Uwagi  
 Położenie i rozmiar kontrolki podrzędnej jest zmienić dynamicznie, po zmianie rozmiaru okna hostowania.  
  
##  <a name="create"></a>CMFCDynamicLayout::Create  
 Przechowuje i weryfikuje okno hosta.  
  
```  
BOOL Create(CWnd* pHostWnd);
```  
  
### <a name="parameters"></a>Parametry  
 pHostWnd  
 Wskaźnik do okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli tworzenie zakończyło się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd  
 Zwraca wskaźnik do okna hosta.  
  
```  
CWnd* GetHostWnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okna hosta.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie wszystkie pozycje formant podrzędny obliczenia względem tego okna.  
  
##  <a name="getminsize"></a>CMFCDynamicLayout::GetMinSize  
 Zwraca rozmiar okna, poniżej którego układ nie jest dostosowywany.  
  
```  
CSize GetMinSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar okna, poniżej którego układ nie jest dostosowywany.  
  
### <a name="remarks"></a>Uwagi  
 Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie podczas zmiany rozmiaru okna hostowania, ale ma minimalny rozmiar, poniżej którego układ nie jest dostosowywany. Użytkownik może zmienić rozmiar okna na mniejszy, ale części okna są następnie ukrywane.  
  
##  <a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect  
 Pobiera prostokąt dla bieżącego obszaru klienckiego okna.  
  
```  
void GetHostWndRect(CRect& rect,);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Po powrocie z funkcji ten parametr zawiera prostokątem obszaru układu. To jest parametrem wyjściowym; wartość wejściowa jest zastępowany.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hasitem"></a>CMFCDynamicLayout::HasItem  
 Sprawdza, czy formant podrzędny został dodany do układ dynamiczny.  
  
```  
BOOL HasItem(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hwnd`  
 Uchwytu okna dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli układu ma już ten element; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isempty"></a>CMFCDynamicLayout::IsEmpty  
 Sprawdza, czy układ dynamiczny ma nie okien podrzędnych dodane.  
  
```  
BOOL IsEmpty();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli układ nie zawiera żadnych elementów; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="loadresource"></a>CMFCDynamicLayout::LoadResource  
 Odczytuje układ dynamiczny z zasobów AFX_DIALOG_LAYOUT, a następnie stosuje układ okna hosta.  
  
```  
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);  
```  
  
### <a name="parameters"></a>Parametry  
 `pHostWnd`  
 Wskaźnik do okna hosta.  
  
 `lpResource`  
 Wskaźnik do buforu, który zawiera zasób AFX_DIALOG_LAYOUT.  
  
 `dwSize`  
 Rozmiar buforu w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest załadowany i stosowane do okna hosta; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movehorizontal"></a>CMFCDynamicLayout::MoveHorizontal  
 Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.  
  
```  
static MoveSettings MoveHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany przenieść wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movehorizontalandvertical"></a>CMFCDynamicLayout::MoveHorizontalAndVertical  
 Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.  
  
```  
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nXRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna hosta.  
  
 `nYRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany przenieść wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movenone"></a>CMFCDynamicLayout::MoveNone  
 Pobiera [MoveSettings](#movesettings_structure) wartość, która reprezentuje nie ruchu pionowych lub poziomych formantu podrzędnego.  
  
```  
static MoveSettings MoveNone();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [MoveSettings](#movesettings_structure) wartość, która rozwiązuje formantu w miejscu, tak aby nie przenosi się jako użytkownik zmienia rozmiar okna hosta.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movesettings_structure"></a>Struktura CMFCDynamicLayout::MoveSettings  
 Hermetyzuje przenoszenia danych dla formantów dynamicznych układu.  
  
```  
struct CMFCDynamicLayout::MoveSettings;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest to klasa zagnieżdżona wewnątrz `CMFCDynamicLayout`.  

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal
Sprawdź, jeśli przenoszenia danych określa niezerową przenoszenia poziomej.  
  

```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `MoveSettings` obiektu określa niezerową przenoszenia poziomych.  

 ## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone
 Sprawdź, jeśli przenoszenia danych określa ma ruchu.  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `MoveSettings` obiektu określa ma ruchu.  

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical
  Sprawdź, jeśli przenoszenia danych określa niezerową przepływu pionowej.  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `MoveSettings` obiektu określa niezerową przepływu pionowej.  

##  <a name="movevertical"></a>CMFCDynamicLayout::MoveVertical  
 Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna obsługi.  
  
```  
static MoveSettings MoveVertical(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany przenieść wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setminsize"></a>CMFCDynamicLayout::SetMinSize  
 Ustawia rozmiar okna, poniżej którego układ nie jest dostosowywany.  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Wymagany rozmiar, poniżej którego układ nie jest dostosowywany.  
  
### <a name="remarks"></a>Uwagi  
 Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie podczas zmiany rozmiaru okna hostowania, ale ma minimalny rozmiar, poniżej którego układ nie jest dostosowywany. Użytkownik może zmienić rozmiar okna na mniejszy, ale części okna są następnie ukrywane.  
  
##  <a name="sizehorizontal"></a>CMFCDynamicLayout::SizeHorizontal  
 Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.  
  
```  
static SizeSettings SizeHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna poziomie zmieni się rozmiar, gdy użytkownik zmienia rozmiar okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje stosunek żądany rozmiar.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizehorizontalandvertical"></a>CMFCDynamicLayout::SizeHorizontalAndVertical  
 Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.  
  
```  
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nXRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna poziomie zmieni się rozmiar, gdy użytkownik zmienia rozmiar okna hosta.  
  
 `nYRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna pionie zmieni się rozmiar, gdy użytkownik zmienia rozmiar okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje stosunek żądany rozmiar.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizenone"></a>CMFCDynamicLayout::SizeNone  
 Pobiera [SizeSettings](#sizesettings_structure) wartość, która reprezentuje nie uległ zmianie rozmiar kontrolki podrzędnej.  
  
```  
static SizeSettings SizeNone();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [SizeSettings](#sizesettings_structure) wartość, która rozwiązuje formantu o rozmiarze tak, aby nie zmienia rozmiar jako użytkownik zmienia rozmiar okna hosta.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizesettings_structure"></a>Cmfcdynamiclayout::sizesettings — struktura  
 Hermetyzuje dane zmiany rozmiaru formantów w układzie dynamicznych.  
  
```  
struct CMFCDynamicLayout::SizeSettings;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest to klasa zagnieżdżona wewnątrz `CMFCDynamicLayout`.  

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal
Sprawdza, jeśli dane zmiany rozmiaru Określa poziomy niezerową rozmiaru.  
  
```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `SizeSettings` obiektu określa poziomy niezerową rozmiaru. 

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone
Sprawdza, czy dane zmiany rozmiaru określa bez zmiany rozmiaru.  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `SizeSettings` określa obiekt bez zmiany rozmiaru.  

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical
Sprawdza, jeśli rozmiar danych określa pionowy niezerową rozmiaru.  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `SizeSettings` obiektu określa pionowy niezerową rozmiaru.  

##  <a name="sizevertical"></a>CMFCDynamicLayout::SizeVertical  
 Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej pionie zmieni się rozmiar, gdy użytkownik zmienia rozmiar okna obsługi.  
  
```  
static SizeSettings SizeVertical(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Określa w procentach, jak daleko kontrolka podrzędna pionie zmieni się rozmiar, gdy użytkownik zmienia rozmiar okna hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje stosunek żądany rozmiar.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
