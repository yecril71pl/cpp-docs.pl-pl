---
title: MODEL COM MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MFC COM (MFC)
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd9035c7b80b36e8124c827c0b3d1b76c59deb52
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="mfc-com"></a>MFC COM
Podzbiór MFC zaprojektowano w celu obsługi modelu COM, podczas gdy większość Active biblioteki szablonu (ATL) jest przeznaczony dla modelu COM programowania. Tematy w tej części opisano Obsługa MFC dla modelu COM.  
  
 Technologie Active (np. ActiveX formantów, zawieranie dokumentów aktywnych OLE i tak dalej) umożliwiają składnik modelu COM. składniki oprogramowania do współdziałać ze sobą w środowisku sieciowym, niezależnie od języka, z którym znajdowały się utworzony. Technologie Active może służyć do tworzenia aplikacji działających na pulpicie lub w Internecie. Aby uzyskać więcej informacji, zobacz [wprowadzenie do COM](../atl/introduction-to-com.md) lub [Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363).  
  
 Aktywne technologie obejmują technologie klienta i serwera, takie jak następujące:  
  
-   [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md), obsługiwane w wersjach MFC 4.2 i później, umożliwia użytkownikom wyświetlanie [dokumenty aktywne](../mfc/active-documents.md) (takich jak pliki programu Microsoft Excel lub Word) i Aktywuj interfejsu całego dokumentu w trybie macierzystym w obszarze klienckim aplikacji [kontenera dokumentów aktywnych](../mfc/active-document-containers.md) takich jak Microsoft Office Binder lub programu Microsoft Internet Explorer. Kontenery działać jako klienci, gdy dokumenty są udostępniane przez [serwery dokumentów aktywnych](../mfc/active-document-servers.md). Aby uzyskać więcej informacji na temat używania dokumenty aktywne w aplikacji internetowych, zobacz: [dokumenty aktywne w Internecie](../mfc/active-documents-on-the-internet.md).  
  
-   Formanty ActiveX są interaktywne obiektów, których można użyć w kontenerach, takich jak witryny sieci Web. Aby uzyskać więcej informacji dotyczących formantów ActiveX zobacz:  
  
    -   [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
    -   [Kontrolki ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md)  
  
    -   [Omówienie: Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [Uaktualnienie istniejącego formantu ActiveX do użycia w Internecie](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [Debugowanie formantu ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   Wykonywanie aktywnych skryptów steruje zachowaniem zintegrowane formantów ActiveX co najmniej jeden z przeglądarki lub serwera. Aby uzyskać więcej informacji na wykonywanie aktywnych skryptów, zobacz [Technologia Active w Internecie](../mfc/active-technology-on-the-internet.md).  
  
-   [Automatyzacja](../mfc/automation.md) (wcześniej znane jako automatyzacji OLE) umożliwia jednej aplikacji do modyfikowania obiektów w innej aplikacji lub "prezentować" obiekty co może manipulować.  
  
     Automatyczne obiektu może być lokalnym lub zdalnym (na innej maszynie jest dostępny w sieci). Automatyzacja jest dostępna dla obiektów COM i OLE.  
  
-   Ta sekcja zawiera również informacje dotyczące programowania składników COM za pomocą MFC, na przykład w [punkty połączenia](../mfc/connection-points.md).  
  
 Omówienie nadal tzw OLE i co nosi teraz nazwę technologii active, zobacz tematy na [OLE](../mfc/ole-in-mfc.md).  
  
 Ponadto zobacz artykuł bazy wiedzy Knowledge Base Q248019: Porada: zapobiec zajęty okna dialogowego pole z pojawiające się podczas długich COM działanie serwera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)  
  
 [Automatyzacja](../mfc/automation.md)  
  
 [Punkty połączenia](../mfc/connection-points.md)  
  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)

