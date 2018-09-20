---
title: Identyfikatory poleceń standardowych i okien | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2106312bd83edc4a37c904e2ee87ce78acb82904
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379134"
---
# <a name="standard-command-and-window-ids"></a>Identyfikatory poleceń standardowych i okien

Bibliotekę Microsoft Foundation Class definiuje kilka poleceń standardowych i okien identyfikatorów w Afxres.h. Te identyfikatory są najczęściej używane w ramach edytory zasobów i w oknie właściwości do mapowania funkcji obsługi wiadomości. Wszystkie standardowe polecenia mają **ID_** prefiks. Na przykład korzystając z Edytora menu, możesz normalnie powiązać element menu Otwórz plik standardowy identyfikator id_file_open — polecenia.

Dla większości standardowych poleceń kod aplikacji nie musi odwoływać się do Identyfikatora polecenia, ponieważ framework sam w sobie obsługuje polecenia za pomocą mapy komunikatów w jej klasy podstawowej framework (`CWinThread`, `CWinApp`, `CView`, `CDocument`, i itd.).

Oprócz identyfikatory poleceń standardowych szereg innych standardowych identyfikatory są zdefiniowane, które mają prefiks z **AFX_ID**. Te identyfikatory zawiera identyfikatorów standardowego okna (prefiks **AFX_IDW_**), ciąg identyfikatorów (prefiks **AFX_IDS_**) i kilka innych typów.

Identyfikatory, które zaczynają się od **AFX_ID** prefiks są rzadko używane przez programistów, ale może być konieczne do odwoływania się do tych identyfikatorów, podczas zastępowania framework funkcje, które również odwołują się do **AFX_ID**s.

Identyfikatory nie są indywidualnie udokumentowano w ramach tego odwołania. Więcej informacji na temat ich można znaleźć w sekcji Uwagi techniczne dotyczące [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), i [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  Plik nagłówkowy Afxres.h pośrednio znajduje się w Afxwin.h. W pliku skryptu (.rc) zasobów w aplikacji należy jawnie przypisać następującą instrukcję:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
