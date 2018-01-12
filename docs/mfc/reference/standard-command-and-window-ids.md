---
title: "Identyfikatory poleceń standardowych i okien | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c8195b1ab967a0d6692e839b1db1e89ee6694d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="standard-command-and-window-ids"></a>Identyfikatory poleceń standardowych i okien
Microsoft Foundation Class Library definiuje liczbę poleceń standardowych i okien identyfikatorów w Afxres.h. Te identyfikatory są najczęściej używane w ramach edytory zasobów i w oknie właściwości do mapowania funkcji obsługi wiadomości. Wszystkie standardowe polecenia mają **ID_** prefiks. Na przykład, korzystając z Edytora menu, zwykle powiąże Otwieranie pliku element menu dla standardowego `ID_FILE_OPEN` polecenia identyfikatora.  
  
 Większość standardowych poleceń kod aplikacji nie musi odwoływać się do Identyfikatora polecenia, ponieważ framework, sama obsługuje polecenia przy użyciu mapy komunikatów w jej klasy podstawowej framework ( `CWinThread`, `CWinApp`, < c4 > `CView` , **CDocument**i tak dalej).  
  
 Oprócz identyfikatory poleceń standardowych liczba innych standardowych identyfikatorów są zdefiniowane, które mają prefiks z **AFX_ID**. Te identyfikatory zawiera standardowe okno identyfikatorów (prefiks **AFX_IDW_**), string identyfikatorów (prefiks **AFX_IDS_**) i kilka innych typów.  
  
 Identyfikatory, które zaczynają się od **AFX_ID** prefiks są rzadko używane przez programistów, ale może być konieczne w celu odwołania się do tych identyfikatorów podczas zastępowania framework funkcje, które należy także zapoznać się **AFX_ID**s.  
  
 Identyfikatory nie są indywidualnie udokumentowane w niniejszej dokumentacji. Więcej informacji na temat ich można znaleźć w Uwagi techniczne [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), i [22](../../mfc/tn022-standard-commands-implementation.md).  
  
> [!NOTE]
>  Plik nagłówka Afxres.h pośrednio znajduje się w Afxwin.h. W pliku skryptu (.rc) zasobu aplikacji należy jawnie przypisać następująca instrukcja:  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
