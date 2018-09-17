---
title: Kreator okna dialogowego ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a10d97d366203da8addbff45a436094abc384cb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710128"
---
# <a name="atl-dialog-wizard"></a>Kreator okna dialogowego ATL

Ten kreator wstawia do projektu obiekt okno dialogowe ATL, pochodzące z [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Okno dialogowe pochodną `CAxDialogImpl` może obsługiwać formantów ActiveX.

Kreator utworzy zasobu okna dialogowego z domyślną **OK** i **anulować** przycisków. Możesz edytować zasobu okna dialogowego i dodawanie kontrolek ActiveX przy użyciu [Edytor okien dialogowych](../../windows/dialog-editor.md) w widoku zasobów.

Kreator wstawia do pliku nagłówka [mapy komunikatów](../../atl/message-maps-atl.md) i deklaracji w zakresie obsługi domyślnie zdarzenia kliknięcia. Zobacz [Implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md) uzyskać więcej informacji dotyczących biblioteki ATL, okno dialogowe.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu okna dialogowego ATL. Podana nazwa określa nazwę klasy i nazwy (.cpp i .h) plików, chyba że zmienił się tych pól indywidualnie.

- **Class**

   Ustawia nazwę klasy, która ma zostać utworzony. Ta nazwa jest na podstawie nazwy podane **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

## <a name="see-also"></a>Zobacz też

[Okno dialogowe ATL](../../atl/reference/adding-an-atl-dialog-box.md)

