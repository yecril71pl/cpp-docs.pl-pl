---
title: Identyfikatory poleceń standardowych i okien
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372958"
---
# <a name="standard-command-and-window-ids"></a>Identyfikatory poleceń standardowych i okien

Biblioteka klas Programu Microsoft Foundation definiuje szereg standardowych identyfikatorów poleceń i okien w pliku Afxres.h. Te identyfikatory są najczęściej używane w edytorach zasobów i [Kreatorze klas](mfc-class-wizard.md) do mapowania wiadomości do funkcji obsługi. Wszystkie standardowe polecenia mają **prefiks ID_.** Na przykład podczas korzystania z edytora menu element menu Otwieranie pliku jest zwykle powiązany ze standardowym identyfikatorem polecenia ID_FILE_OPEN.

W przypadku większości standardowych poleceń kod aplikacji nie musi odwoływać się do identyfikatora polecenia, ponieważ sama struktura`CWinThread` `CWinApp`obsługuje `CView` `CDocument`polecenia za pośrednictwem map komunikatów w swoich podstawowych klasach framework ( , , , i tak dalej).

Oprócz standardowych identyfikatorów poleceń zdefiniowano szereg innych standardowych identyfikatorów, które mają prefiks **AFX_ID**. Te identyfikatory obejmują standardowe identyfikatory okien (prefiks **AFX_IDW_),** identyfikatory ciągów (prefiks **AFX_IDS_)** i kilka innych typów.

Identyfikatory, które zaczynają się od prefiksu **AFX_ID** są rzadko używane przez programistów, ale może być konieczne odwoływanie się do tych identyfikatorów podczas zastępowania funkcji struktury, które również odnoszą się do **AFX_ID**s.

Identyfikatory nie są indywidualnie udokumentowane w tym odwołaniu. Więcej informacji na ich temat można znaleźć w uwagach technicznych [20,](../../mfc/tn020-id-naming-and-numbering-conventions.md) [21](../../mfc/tn021-command-and-message-routing.md)i [22.](../../mfc/tn022-standard-commands-implementation.md)

> [!NOTE]
> Plik nagłówka Afxres.h jest pośrednio zawarty w Afxwin.h. W pliku skryptu zasobów aplikacji należy jawnie dołączyć następującą instrukcję:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
