---
title: "Klasy i wątki ODBC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1d1d922dfc34fa3e5530eca77a6501ad3e331fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-classes-and-threads"></a>Klasy i wątki ODBC
Począwszy od MFC 4.2, jest obsługa wielowątkowości w przypadku klas MFC ODBC. Należy jednak pamiętać, że MFC nie zapewnia obsługi wielowątkowości dla klasy DAO.  
  
 Obsługa wielowątkowości w przypadku klasy ODBC ma pewne ograniczenia. Ponieważ te klasy zawijać interfejsu API ODBC, są one ograniczone do obsługi wielowątkowości składników, na których są tworzone. Na przykład wiele sterowników ODBC nie są wątkowo; w związku z tym klasach MFC ODBC nie są wątkowo korzystania z jednego z tych sterowników. Należy sprawdzić, czy sterownik określonego jest bezpieczne wątkowo.  
  
 Podczas tworzenia aplikacji wielowątkowych, należy zwrócić szczególną uwagę przy użyciu wielu wątków do modyfikowania tego samego obiektu. Na przykład korzystającej z tego samego `CRecordset` obiektu w dwóch wątków może spowodować problemy podczas pobierania danych; operację pobierania w jeden wątek może dojść do zastąpienia danych pobranych w innym wątku. Najczęściej używana klas MFC ODBC w oddzielnych wątkach jest udostępnienie otwarty `CDatabase` obiektu pomiędzy wątkami do tego samego połączenia ODBC, za pomocą oddzielnego `CRecordset` obiektu w każdym wątku. Należy pamiętać, że nie należy przekazać nieotwarte `CDatabase` do obiektu `CRecordset` obiektu w innym wątku.  
  
> [!NOTE]
>  Jeśli wiele wątków manipulowania tego samego obiektu, należy zaimplementować mechanizmów odpowiedniej synchronizacji, takie jak sekcje krytyczne. Należy pamiętać, że niektóre operacje, takie jak **Otwórz**, nie są chronione. Należy się upewnić, że te operacje nie zostanie wywołana jednocześnie z oddzielnych wątkach.  
  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji wielowątkowych, zobacz [wielowątkowość tematy](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz połączenie z bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Dostęp do danych programowania (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)