---
title: Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 9bfb907d21c928c605b304c595acb834d0046e35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209056"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC)

`CRecordView` udostępnia domyślne programy obsługi aktualizacji interfejsu użytkownika dla poleceń nawigacyjnych. Te programy obsługi automatyzują Włączanie i wyłączanie obiektów interfejsu użytkownika — elementy menu i przyciski paska narzędzi. Kreator aplikacji dostarcza menu standardowe i, jeśli wybierzesz opcję **paska narzędzi było dokować** , zestaw przycisków paska narzędzi dla poleceń. Jeśli tworzysz klasę widoku rekordu przy użyciu `CRecordView`, możesz chcieć dodać podobne obiekty interfejsu użytkownika do aplikacji.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>Aby utworzyć zasoby menu za pomocą edytora menu

1. Aby uzyskać informacje o używaniu [edytora menu](../windows/menu-editor.md), Utwórz własne menu z tymi samymi czterema poleceniami.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Aby utworzyć przyciski paska narzędzi przy użyciu edytora grafiki

1. Aby uzyskać informacje o używaniu [edytora pasków narzędzi](../windows/toolbar-editor.md), Edytuj zasób paska narzędzi, aby dodać przyciski paska narzędzi dla poleceń nawigacyjnych nagrywania.

## <a name="see-also"></a>Zobacz też

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Korzystanie z widoku rekordu](../data/using-a-record-view-mfc-data-access.md)
