---
title: Klasy i wątki ODBC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a7b78284b1fc0bd952928952c24c61423396eb2
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341052"
---
# <a name="odbc-classes-and-threads"></a>Klasy i wątki ODBC
Począwszy od MFC 4.2 jest obsługa wielowątkowości w przypadku klas MFC ODBC. Należy jednak pamiętać, że MFC nie zapewnia obsługi wielowątkowości dla klas DAO.  
  
 Obsługa wielowątkowości w przypadku klasy ODBC ma pewne ograniczenia. Ponieważ klasy te zawijać interfejsu API ODBC, są one ograniczone do obsługi wielowątkowości składników, na których zostały one utworzone. Na przykład wiele sterowników ODBC nie jest metodą o bezpiecznych wątkach; w związku z tym klasach MFC ODBC nie są wątkowo korzystania z jednej z tych sterowników. Należy sprawdzić, czy określonego sterownika jest metodą o bezpiecznych wątkach.  
  
 Podczas tworzenia aplikacji wielowątkowych, powinno być dużą ostrożność podczas przy użyciu wielu wątków do manipulowania tego samego obiektu. Na przykład, korzystając z tych samych `CRecordset` obiektu w dwa wątki, które mogą powodować problemy podczas pobierania danych; operację pobierania w jeden wątek może zastąpić dane pobierane w innym wątku. Częściej spotykanym sposobem wykorzystania klas MFC ODBC w oddzielnych wątkach jest udostępnienie otwartą `CDatabase` obiektu w wątkach, aby użyć tego samego połączenia ODBC za pomocą oddzielnego `CRecordset` obiektów każdego wątku. Należy pamiętać, że użytkownik nie mają być przekazywane nieotwarte `CDatabase` obiekt `CRecordset` obiektu w innym wątku.  
  
> [!NOTE]
>  Jeśli konieczne jest posiadanie wielu wątków, manipulowania tego samego obiektu, powinien implementować synchronizacji odpowiednich mechanizmów, takich jak sekcje krytyczne. Należy pamiętać, że niektóre operacje, takie jak `Open`, nie są chronione. Należy się upewnić, że te operacje nie zostaną wywołane jednocześnie z oddzielnych wątkach.  
  
 Aby uzyskać więcej informacji o tworzeniu aplikacji wielowątkowych, zobacz [tematy o wielowątkowości](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Programowanie (MFC/ATL) dostępu do danych](../../data/data-access-programming-mfc-atl.md)