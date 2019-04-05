---
title: Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: de94b28e713459edfd63aff832caecc7ea49ca33
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023363"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC)

`CRecordView` udostępnia domyślne programy obsługi aktualizacji interfejsu użytkownika dla poleceń nawigacji. Te procedury obsługi automatyzacji, włączanie i wyłączanie obiektów interfejsu użytkownika — elementy menu i przycisków na pasku narzędzi. Kreator aplikacji dostarcza menu standardowe i, jeśli wybierzesz **Dokowalne narzędzi** opcję zestaw przycisków paska narzędzi dla poleceń. Jeśli utworzysz przy użyciu klas widoków rekordów `CRecordView`, możesz zechcieć dodać podobne obiekty interfejsu użytkownika do aplikacji.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>Aby utworzyć menu zasobów za pomocą menu Edytor

1. Odwołujące się do informacji o używaniu [Edytor menu](../windows/menu-editor.md), utworzyć własne menu przy użyciu tych samych poleceń cztery.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Aby utworzyć przyciski paska narzędzi z grafiki, Edytor

1. Odwołujące się do informacji o używaniu [Edytor paska narzędzi](../windows/toolbar-editor.md), Edytuj zasób paska narzędzi, aby dodać przyciski paska narzędzi dla poleceń nawigacji między rekordami.

## <a name="see-also"></a>Zobacz także

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)