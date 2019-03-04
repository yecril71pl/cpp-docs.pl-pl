---
title: 'Podstawy OLE: Łączenie i osadzanie'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 02607df2a8fa086c5751f2b446e349a3efdbcd20
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280969"
---
# <a name="ole-background-linking-and-embedding"></a>Podstawy OLE: Łączenie i osadzanie

Za pomocą polecenia wklejania w aplikacji kontenera można utworzyć składnika osadzonego lub osadzonego elementu. Źródło danych pod kątem osadzonego elementu jest przechowywane jako część dokumentu OLE, który go zawiera. W ten sposób plik dokumentu do dokumentu edytora tekstów może zawierać tekst i także może zawierać, mapy bitowe, wykresy, formuły lub dowolny inny typ danych.

OLE udostępnia inny sposób, aby uwzględniać dane z innych aplikacji: tworzenie połączony składnik lub połączony element lub łącza. Procedury służące do tworzenia połączonego elementu są podobne do tworzenia element osadzony, z tą różnicą, że należy użyć polecenia Wklej łącze zamiast polecenie Paste. W przeciwieństwie do składnika osadzonego połączony składnik przechowuje ścieżkę do oryginalnych danych odbywa się w oddzielnym pliku.

Na przykład jeśli pracujesz w programie dokumentu procesora i utworzyć połączony element, aby niektóre komórki arkusza kalkulacyjnego, dane, które dla połączonego elementu są przechowywane w oryginalnym dokumencie arkusza kalkulacyjnego. Dokument edytora tekstów zawiera tylko te informacje, określając, gdzie element zostanie znaleziony, oznacza to, zawiera łącze do oryginalnego dokumentu arkusza kalkulacyjnego. Dwukrotne kliknięcie komórki arkusza kalkulacyjnego aplikacja zostanie uruchomiona, a w oryginalnym dokumencie arkusza kalkulacyjnego jest ładowany z którym została zapisana.

Każdy element OLE, czy osadzony lub połączony, ma typ skojarzone z nią na podstawie aplikacji, w której został utworzony. Na przykład element Paintbrush firmy Microsoft jest jeden typ elementu, a element programu Microsoft Excel jest innego typu. Jednak niektóre aplikacje, można utworzyć więcej niż jeden typ elementu. Na przykład program Microsoft Excel można utworzyć elementy arkusza, elementów wykresu i elementy arkusz makr. Każdy z tych elementów można jednoznacznie zidentyfikować przez system za pomocą identyfikatora klasy lub **CLSID**.

## <a name="see-also"></a>Zobacz także

[Podstawy OLE](../mfc/ole-background.md)<br/>
[Podstawy OLE: Kontenery i serwery](../mfc/ole-background-containers-and-servers.md)<br/>
[Kontenery: Elementy klienckie](../mfc/containers-client-items.md)<br/>
[Serwery: Elementy serwera](../mfc/servers-server-items.md)
