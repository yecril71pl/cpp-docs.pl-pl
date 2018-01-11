---
title: Klasa CMFCToolBarFontSizeComboBox | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ba8dde4142cff3606cc2b5ad1861096637f68c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Klasa CMFCToolBarFontSizeComboBox
Przycisk paska narzędzi, który zawiera kontrolki pola kombi, które umożliwia użytkownikowi wybranie rozmiaru czcionki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Konstruuje `CMFCToolBarFontSizeComboBox` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Zwraca wybrany rozmiar czcionki w twipach.|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Wstawia listy pola kombi wszystkich rozmiarów czcionek obsługiwanych dla określonej czcionki.|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Ustawia rozmiar czcionki w twipach.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `CMFCToolBarFontSizeComboBox` obiekt razem z [klasy CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) obiekt, aby umożliwić użytkownikowi wybranie czcionki i rozmiar czcionki.  
  
 Tak samo, jak dodać przycisk pole kombi czcionki, można dodać przycisk pole kombi rozmiar czcionki do paska narzędzi. Aby uzyskać więcej informacji, zobacz [CMFCToolBarFontComboBox klasy](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
 Gdy użytkownik wybierze nowy czcionkę w `CMFCToolBarFontComboBox` obiektu, możesz wypełnić pole kombi rozmiar czcionki obsługiwane rozmiary czcionki za pomocą [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCToolBarFontSizeComboBox` klasa do konfigurowania `CMFCToolBarFontSizeComboBox` obiektu. Jak pobrać rozmiar czcionki w twipach z pola tekstowego, wypełnienie pola kombi rozmiar czcionki wszystkie prawidłowe rozmiary czcionki danego i określ rozmiar czcionki w twipach pokazano w przykładzie. Następujący fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 Konstruuje `CMFCToolBarFontSizeComboBox` obiektu.  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize  
 Pobiera rozmiar czcionki w twipach, w polu tekstowym pola kombi rozmiar czcionki.  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość zwracana jest dodatnia, to rozmiar czcionki w twipach. Jeśli w polu tekstowym pola kombi jest pusta, wynosi -1. W przypadku wystąpienia błędu jest -2.  
  
##  <a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 Wstawia wszystkie prawidłowe rozmiary czcionki danego pola kombi rozmiar czcionki.  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] strFontName`  
 Określa nazwę czcionki.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, jeśli chcesz synchronizować między zaznaczenia w polu kombi czcionki i rozmiar czcionki kombi, takich jak [CMFCToolBarFontComboBox klasy](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
##  <a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize  
 Zaokrąglenie określony rozmiar (w twipach) do najbliższej rozmiar w punktach, a następnie ustawia wybranym rozmiarze w polu kombi z tą wartością.  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nSize`  
 Określa rozmiar czcionki (w twipach), aby ustawić.  
  
### <a name="remarks"></a>Uwagi  
 Poprzedni rozmiar poprawną czcionkę można pobrać później przez wywołanie metody [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



