---
title: 'Podstawy OLE: Łączenie i osadzanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5dc7a5770c98323187dbabcd8c2a7bb9eb652de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ole-background-linking-and-embedding"></a>Podstawy OLE: łączenie i osadzanie
Za pomocą polecenia wklejania w aplikacji kontenera można utworzyć składnika osadzonego lub element osadzony. Źródło danych pod kątem element osadzony jest przechowywana jako część dokumentu OLE, który go zawiera. W ten sposób plik dokumentu do dokumentu edytora tekstów mogą zawierać tekst i również może zawierać mapy bitowe, wykresy, formuły lub typu danych.  
  
 OLE zawiera inny sposób danych z innej aplikacji: Tworzenie składnika połączonego lub połączony element lub łącze. Kroki tworzenia połączonego elementu są podobne jak w przypadku tworzenia element osadzony z tą różnicą, że zamiast polecenia Wklej za pomocą polecenia Wklej łącze. W przeciwieństwie do składnika osadzonego połączony składnik przechowuje ścieżkę do oryginalnych danych, która jest często w osobnym pliku.  
  
 Na przykład jeśli pracujesz w programie dokumentu procesora i tworzenie połączonego elementu do niektóre komórki arkusza kalkulacyjnego, dane do połączonego elementu znajduje się w oryginalnym dokumencie arkusza kalkulacyjnego. Dokument edytora tekstów zawiera tylko te informacje, określając, gdzie element zostanie znaleziony, oznacza to, zawiera łącze do oryginalnego dokumentu arkusza kalkulacyjnego. Po dwukrotnym kliknięciu komórki arkusza kalkulacyjnego aplikacja jest uruchamiana i oryginalnego dokumentu arkusza kalkulacyjnego są ładowane z którym był przechowywany.  
  
 Każdy element OLE osadzony czy połączony, ma typ skojarzony z nim na podstawie aplikacji, który go utworzył. Na przykład element Paintbrush firmy Microsoft jest jeden typ elementu, a element programu Microsoft Excel jest innego typu. Jednak niektóre aplikacje, można utworzyć więcej niż jeden typ elementu. Na przykład program Microsoft Excel można utworzyć obiekty arkusza, elementów wykresu i elementy arkusz makr. Każdy z tych elementów można unikatowo identyfikowana przez system za pomocą identyfikatora klasy lub **CLSID**.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy OLE](../mfc/ole-background.md)   
 [Podstawy OLE: Kontenery i serwery](../mfc/ole-background-containers-and-servers.md)   
 [Kontenery: Elementy klienckie](../mfc/containers-client-items.md)   
 [Serwery: elementy serwera](../mfc/servers-server-items.md)

