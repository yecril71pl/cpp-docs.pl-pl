---
title: Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 43f5d1017b3f89474e9dd7eebce0cf71c8c8c448
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086879"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC)

`CRecordView` udostępnia domyślne programy obsługi aktualizacji interfejsu użytkownika dla poleceń nawigacji. Te procedury obsługi automatyzacji, włączanie i wyłączanie obiektów interfejsu użytkownika — elementy menu i przycisków na pasku narzędzi. Kreator aplikacji dostarcza menu standardowe i, jeśli wybierzesz **Dokowalne narzędzi** opcję zestaw przycisków paska narzędzi dla poleceń. Jeśli utworzysz przy użyciu klas widoków rekordów `CRecordView`, możesz zechcieć dodać podobne obiekty interfejsu użytkownika do aplikacji.  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>Aby utworzyć menu zasobów za pomocą menu Edytor  
  
1. Odwołujące się do informacji o używaniu [Edytor menu](../windows/menu-editor.md), utworzyć własne menu przy użyciu tych samych poleceń cztery.  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Aby utworzyć przyciski paska narzędzi z grafiki, Edytor  
  
1. Odwołujące się do informacji o używaniu [Edytor paska narzędzi](../windows/toolbar-editor.md), Edytuj zasób paska narzędzi, aby dodać przyciski paska narzędzi dla poleceń nawigacji między rekordami.  
  
## <a name="see-also"></a>Zobacz też  

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)