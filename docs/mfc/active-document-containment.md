---
title: "Zawieranie dokumentów aktywnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 749d4badb3a7b5a2c61fa753a840765f14e2a329
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="active-document-containment"></a>Zawieranie dokumentów aktywnych
Zawieranie dokumentów aktywnych jest technologia, która udostępnia jeden ramki, w której do pracy z dokumentami, zamiast wymuszania wielokrotnego do utworzenia i użycia wielu klatek aplikacji dla każdego typu dokumentu. Różni się z podstawową technologię OLE w tym OLE współpracuje z obiektami osadzonego wewnątrz złożonego dokumentu, w którym mogą być aktywne tylko jednego fragmentu zawartości. W kontekście jedną ramkę z zawieranie dokumentów aktywnych aktywowania całego dokumentu (to znaczy całej aplikacji, w tym skojarzone menu, paski narzędzi i tak dalej).  
  
 Microsoft Office zaimplementować Office Binder pierwotnie opracowano technologii zawierania dokumentów aktywnych. Jednak technologii jest wystarczająco elastyczny, aby obsługiwać kontenery dokumentów aktywnych niż Office Binder i może obsługiwać serwery dokumentu, innych niż aplikacje pakietu Office i zgodne z pakietem Office.  
  
 Nosi nazwę aplikacji, która obsługuje dokumenty aktywne [kontenera dokumentów aktywnych](../mfc/active-document-containers.md). Przykładami takich kontenery są Microsoft Office Binder lub programu Microsoft Internet Explorer.  
  
 Zawieranie dokumentów aktywnych jest implementowany jako zestaw rozszerzeń OLE dokumentów technologii złożonego dokumentu OLE. Rozszerzenia są dodatkowe interfejsy, które umożliwiają obiekt osadzenia, w miejsce, do reprezentowania cały dokument zamiast pojedynczy osadzonej zawartości. Podobnie jak w przypadku dokumentów OLE zawieranie dokumentów aktywnych używa kontenera, w którym miejsce wyświetlania dokumenty aktywne i serwerów, które umożliwiają możliwości interfejsu i manipulowania nimi dokumentów aktywnych się użytkownika.  
  
 [Serwer dokumentów aktywnych](../mfc/active-document-servers.md) jest aplikacji (takich jak Word, Excel lub PowerPoint), która obsługuje co najmniej jednej klasy dokumentów aktywnych, w których każdy obiekt obsługuje interfejsy rozszerzenia, które umożliwiają obiektu aktywacji w odpowiedniego kontenera.  
  
 [Dokumentów aktywnych](../mfc/active-documents.md) (udostępnione z serwer dokumentów aktywnych, takich jak Word czy Excel) jest zasadniczo dobrym przybliżeniem pełnego, z konwencjonalnej dokument, który jest osadzony jako obiekt w ramach innego kontenera dokumentów aktywnych. W przeciwieństwie do osadzonych obiektów active dokumenty mają pełną kontrolę nad ich stron, a pełna interfejs aplikacji (z wszystkie jego polecenia i narzędzia) jest dostępny dla użytkownika, aby je edytować.  
  
 Dokument aktywny najlepiej jest rozpoznawany przez identyfikujący standardowe osadzonego obiektu OLE. Po Konwencji OLE osadzonego obiektu to taki, który jest wyświetlany na stronie dokumentu, który jest jego właścicielem, a dokumentu jest zarządzana przez kontener OLE. Kontener przechowuje dane osadzonego obiektu z pozostałej części dokumentu. Jednak obiekty osadzone są ograniczone, w tym kontroluje strony, na którym są wyświetlane.  
  
 Użytkownicy aplikacji kontenera dokumentów aktywnych można tworzyć dokumenty aktywne (nazywanych sekcjami Office Binder) przy użyciu ich ulubionych aplikacji (zakładając, że te aplikacje są aktywnego dokumentu. włączone), jeszcze użytkownicy mogą zarządzać Projekt wynikowy jako pojedyncza jednostka, która może być jednoznacznie o nazwie, zapisany wydruku i tak dalej. W taki sam sposób użytkownika przeglądarki internetowej można traktować jako jednostki magazynu pojedynczego dokumentu, umożliwia przeglądanie dokumentów, w tym magazynie z jednej lokalizacji całej sieci, a także systemów pliku lokalnego.  
  
## <a name="sample-programs"></a>Przykładowe programy  
  
-   [MFCBIND](../visual-cpp-samples.md) przykładową wdrożenia aplikacji kontenera dokumentów aktywnych.  
  
## <a name="see-also"></a>Zobacz też  
 [MODEL COM MFC](../mfc/mfc-com.md)

