---
title: 'Schowek: Kopiowanie i wklejanie danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4756da7459f3e584dd02b882f5c790412c095561
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929471"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schowek: kopiowanie i wklejanie danych
W tym temacie opisano minimalną pracy, należy wykonać, kopiowanie i wklejanie ze Schowka w aplikacji OLE. Zaleca się przeczytanie [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) tematy przed kontynuowaniem.  
  
 Przed zaimplementowaniem albo kopiowanie i wklejanie, musisz podać funkcje do obsługi opcji kopiowanie, wycinanie i wklejanie w menu Edycja.  
  
##  <a name="_core_copying_or_cutting_data"></a> Kopiowanie lub wycinanie danych  
  
#### <a name="to-copy-data-to-the-clipboard"></a>Aby skopiować dane do Schowka  
  
1.  Sprawdzenia, czy dane do skopiowania danych natywnych jest element osadzony lub połączony.  
  
    -   Jeśli dane jest osadzony czy połączony, uzyskać wskaźnik do `COleClientItem` obiekt, który został wybrany.  
  
    -   Jeśli dane są natywnych aplikacji jest serwerem, należy utworzyć nowy obiekt pochodną `COleServerItem` zawierający wybranych danych. W przeciwnym razie utwórz `COleDataSource` obiektu danych.  
  
2.  Wywołania wybranego elementu `CopyToClipboard` funkcję elementu członkowskiego.  
  
3.  Jeśli użytkownik wybrał operacji wycinania, zamiast operacji kopiowania, Usuń wybranych danych z aplikacji.  
  
 Aby zapoznać się z przykładem tej sekwencji, zobacz `OnEditCut` i `OnEditCopy` funkcje w OLE MFC przykładowe programy [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md). Należy pamiętać, że te przykłady Obsługa wskaźnik do aktualnie wybrane dane, tak kroku 1 jest już zakończone.  
  
##  <a name="_core_pasting_data"></a> Wklejanie danych  
 Wklejanie danych jest bardziej skomplikowane niż go kopiować, ponieważ trzeba wybrać format używany w wkleić danych do aplikacji.  
  
#### <a name="to-paste-data-from-the-clipboard"></a>Można wkleić danych ze Schowka  
  
1.  W klasie widoku zaimplementować `OnEditPaste` do obsługi użytkowników, wybierając opcję Wklej z menu Edycja.  
  
2.  W `OnEditPaste` funkcji, należy utworzyć `COleDataObject` obiekt i wywołanie jego `AttachClipboard` funkcji członkowskiej, aby połączyć tego obiektu z danych w Schowku.  
  
3.  Wywołanie `COleDataObject::IsDataAvailable` do sprawdzenia, czy określony format jest dostępna.  
  
     Alternatywnie można użyć `COleDataObject::BeginEnumFormats` do wyszukania w innych formatach do momentu znalezienia najbardziej nadaje się do aplikacji.  
  
4.  Wykonaj Wklej formatu.  
  
 Na przykład to działanie, zobacz wykonania `OnEditPaste` funkcje Członkowskie w widoku klas zdefiniowanych w programach MFC OLE próbki [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md).  
  
> [!TIP]
>  Największą zaletą oddzielanie operacji wklejania do odrębnej funkcji jest, że ten sam kod Wklej mogą być używane po upuszczeniu danych w aplikacji podczas operacji przeciągania i upuszczania. Jak OCLIENT i HIERSVR Twoje `OnDrop` także wywołać funkcję `DoPasteItem`, ponowne użycie kodu napisanego w celu wykonania operacji wklejania.  
  
 Aby obsłużyć Wklej specjalne opcji menu Edycja, zobacz temat [okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md).  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)  
  
-   [Źródła danych OLE obiekty i dane oraz uniform transferów danych](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Przeciąganie i upuszczanie OLE](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek: korzystanie z mechanizmu schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

