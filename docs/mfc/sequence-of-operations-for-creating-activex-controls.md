---
title: "Sekwencja operacji przy tworzeniu formantów ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c7034a063856aa059e7c1edf21510b8b993a55ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Sekwencja operacji przy tworzeniu kontrolek ActiveX
W poniższej tabeli przedstawiono roli i roli w ramach tworzenia formantów ActiveX (wcześniej znane jako formantów OLE).  
  
### <a name="creating-activex-controls"></a>Tworzenie formantów ActiveX  
  
|Zadanie|Jak|Jest w ramach|  
|----------|------------|------------------------|  
|Utwórz framework formantu ActiveX.|Uruchom Kreator kontrolek ActiveX MFC do tworzenia formantu. Określ opcje, które mają na stronach opcje. Opcje obejmują typ i nazwa formantu w projekcie, licencjonowanie, podklasy oraz metody pól informacji.|Kreator formantów MFC ActiveX tworzy pliki dla formantu ActiveX z podstawowymi funkcjami, w tym pliki źródłowe dla aplikacji, kontrolowania i strony właściwości lub stron. Plik zasobów; plik projektu; i innych osób, wszystkie dostosowane do specyfikacji.|  
|Zobacz formantu i Kreator kontrolek ActiveX oferują bez dodawania wiersz z własnego kodu.|Tworzenie formantu ActiveX i przetestować go w programie Internet Explorer lub [próbki TSTCON](../visual-cpp-samples.md).|Uruchomione formant ma możliwość zmiany rozmiaru i przenieść. Obejmuje ona również **pól informacji** — metoda (Jeśli wybrano), która może zostać wywołana.|  
|Implementuje metody i właściwości formantu.|Implementowanie właściwości i metod specyficznych dla formantu, dodając funkcje Członkowskie narażonych interfejs do danych formantu. Dodaj zmienne Członkowskie, aby pomieścić struktur danych i wyzwalać zdarzeń po określeniu przy użyciu programów obsługi zdarzeń.|Platformę został już zdefiniowany mapy w celu obsługi zdarzeń, właściwości i metod, pozostawiając pozwala skupić się na implementowania właściwości i metod formantu. Domyślna strona właściwości jest widoczny i podano domyślną metodą pól informacji.|  
|Konstruować strony lub strona właściwości formantu.|Edytory zasobów programu Visual C++ służy do wizualnego edytowania interfejs strony właściwości formantu:<br /><br /> -Utwórz dodatkowe strony właściwości.<br />-Tworzyć i edytować mapy bitowe, ikony i kursory.<br /><br /> Strony właściwości można również sprawdzić w edytorze okien dialogowych.|Domyślny plik zasobów tworzone przez Kreatora aplikacji MFC udostępnia wiele zasobów, które są potrzebne. Visual C++ umożliwia edytowanie istniejących zasobów i dodawanie nowych zasobów łatwo i wizualne.|  
|Przetestuj zdarzeń, metod i właściwości formantu.|Odbuduj formantu i użyć kontenera testu do testowania poprawnie pracować z programów obsługi.|Można wywołać metody kontroli i modyfikowania jej właściwości, za pośrednictwem interfejsu strony właściwości lub kontener testu. Ponadto umożliwia kontener testu Śledź zdarzenia wywoływane z formantu i powiadomienia odbierane przez formantu kontenera.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opieranie się na strukturze](../mfc/building-on-the-framework.md)   
 [Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Sekwencja operacji przy tworzeniu aplikacji bazy danych](../mfc/sequence-of-operations-for-creating-database-applications.md)

