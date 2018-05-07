---
title: Aktualizowanie interfejsu użytkownika dla widoków rekordów (MFC Data Access) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1227ba1fe0a14af7013109b336d1d60eda41137e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizowanie interfejsu użytkownika dla widoków rekordów (dostęp do danych MFC)
`CRecordView` udostępnia domyślny interfejs użytkownika aktualizacji procedury obsługi polecenia nawigacji. Te programy obsługi zdarzeń automatyzacji Włączanie i wyłączanie obiektów interfejsu użytkownika — elementy menu i przycisków paska narzędzi. Kreator aplikacji udostępnia standardowe menu i, w przypadku wybrania **dokującego paska narzędzi** opcję zestaw przycisków paska narzędzi dla poleceń. W przypadku utworzenia klasy widoków rekordów przy użyciu `CRecordView`, można dodać podobne obiekty interfejsu użytkownika do aplikacji.  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>Aby utworzyć zasoby menu za pomocą menu edytora  
  
1.  Odwołujących się do informacji o używaniu [edytora menu](../windows/menu-editor.md), utworzyć własne menu za pomocą tego samego cztery poleceń.  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Aby utworzyć z grafiki przycisków paska narzędzi edytora  
  
1.  Odwołujących się do informacji o używaniu [paska narzędzi edytora](../windows/toolbar-editor.md), Edytuj dodawanie przycisków paska narzędzi dla poleceń nawigacji rekordu zasobu paska narzędzi.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)