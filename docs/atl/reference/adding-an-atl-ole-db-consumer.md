---
title: Dodawanie konsumenta OLE DB ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 41e31e82c97252a2ab5e34a78db5af1fd4e24f98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-an-atl-ole-db-consumer"></a>Dodawanie konsumenta OLE DB ATL
Ten kreator umożliwia dodawanie konsumenta ATL OLE DB do projektu. Konsumenta ATL OLE DB składa się z OLE DB akcesor klasy danych powiązania i trzeba uzyskiwać dostęp do źródła danych. Projekt musi być utworzony jako aplikacji ATL COM lub MFC lub Win32 aplikacji z obsługą ATL (która automatycznie dodaje OLE DB Kreator konsumenta ATL).  
  
 **Uwaga** konsumenta OLE DB można dodać do projektu MFC. Jeśli to zrobisz, OLE DB Kreator konsumenta ATL dodaje niezbędne obsługi modelu COM do projektu. Przy założeniu, że po utworzeniu projektu MFC wybrane **formantów ActiveX** pole wyboru (w **funkcje zaawansowane** Kreatora aplikacji MFC projektu), który jest domyślnie zaznaczone. Wybranie tej opcji gwarantuje, że aplikacja wywołuje **CoInitialize** i **CoUninitialize**. Jeśli nie wybrano **formantów ActiveX** podczas tworzenia projektu MFC, należy wywołać **CoInitialize** i **CoUninitialize** w kodzie głównego.  
  
### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Aby dodać do projektu konsumenta ATL OLE DB  
  
1.  W widoku klas kliknij prawym przyciskiem myszy projekt. W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj klasę**.  
  
2.  W folderze Visual C++, kliknij dwukrotnie **OLE DB konsumenta ATL** ikony lub zaznacz go i kliknij **Otwórz**.  
  
     OLE DB Kreator konsumenta ATL zostanie otwarty.  
  
3.  Zdefiniuj ustawienia, zgodnie z opisem w [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).  
  
4.  Kliknij przycisk **Zakończ** aby zamknąć kreatora. Nowo utworzony kod konsumenta OLE DB zostanie wstawiony w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)

