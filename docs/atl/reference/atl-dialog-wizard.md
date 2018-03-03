---
title: Kreator okna dialogowego ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6cdf16b3e82ce69fa06b3eacda8d7b48643fb3c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-dialog-wizard"></a>Kreator okna dialogowego ATL
Ten kreator wstawia do projektu obiekt okno dialogowe ATL, pochodzący od [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Okno dialogowe pochodną `CAxDialogImpl` może obsługiwać formantów ActiveX.  
  
 Kreator tworzy zasób okna dialogowego z domyślnymi **OK** i **anulować** przycisków. Możesz edytować zasobu okna dialogowego i Dodaj formanty ActiveX przy użyciu [Edytor okien dialogowych](../../windows/dialog-editor.md) w widoku zasobów.  
  
 Kreator wstawia do pliku nagłówka [mapy komunikatów](../../atl/message-maps-atl.md) i deklaracje domyślnie obsługi zdarzenia kliknięcia. Zobacz [implementacja okno dialogowe](../../atl/implementing-a-dialog-box.md) uzyskać więcej informacji o ATL okien dialogowych.  
  
 **Krótka nazwa**  
 Ustawia skróconą nazwę obiektu okna dialogowego ATL. O podanej nazwie Określa nazwę klasy i nazwy (.cpp i .h) plików, jeśli nie zmienisz tych pól pojedynczo.  
  
 `Class`  
 Ustawia nazwę klasy, która ma być utworzony. Ta nazwa jest na podstawie nazwy podane **krótką nazwę**, poprzedzającą "C", typowy prefiks nazwy klasy.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno dialogowe ATL](../../atl/reference/adding-an-atl-dialog-box.md)

