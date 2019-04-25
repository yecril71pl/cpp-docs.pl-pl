---
title: Identyfikatory poleceń standardowych i okien
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: e5f6955407f565d5cc06ef57e9bd273f6c0f7712
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310054"
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

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
