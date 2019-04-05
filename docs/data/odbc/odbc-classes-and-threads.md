---
title: Klasy i wątki ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 2d11cdab632e916f548011462f9738bc267fc730
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023533"
---
# <a name="odbc-classes-and-threads"></a>Klasy i wątki ODBC

Począwszy od MFC 4.2 jest obsługa wielowątkowości w przypadku klas MFC ODBC. Należy jednak pamiętać, że MFC nie zapewnia obsługi wielowątkowości dla klas DAO.

Obsługa wielowątkowości w przypadku klasy ODBC ma pewne ograniczenia. Ponieważ klasy te zawijać interfejsu API ODBC, są one ograniczone do obsługi wielowątkowości składników, na których zostały one utworzone. Na przykład wiele sterowników ODBC nie jest metodą o bezpiecznych wątkach; w związku z tym klasach MFC ODBC nie są wątkowo korzystania z jednej z tych sterowników. Należy sprawdzić, czy określonego sterownika jest metodą o bezpiecznych wątkach.

Podczas tworzenia aplikacji wielowątkowych, powinno być dużą ostrożność podczas przy użyciu wielu wątków do manipulowania tego samego obiektu. Na przykład, korzystając z tych samych `CRecordset` obiektu w dwa wątki, które mogą powodować problemy podczas pobierania danych; operację pobierania w jeden wątek może zastąpić dane pobierane w innym wątku. Częściej spotykanym sposobem wykorzystania klas MFC ODBC w oddzielnych wątkach jest udostępnienie otwartą `CDatabase` obiektu w wątkach, aby użyć tego samego połączenia ODBC za pomocą oddzielnego `CRecordset` obiektów każdego wątku. Należy pamiętać, że użytkownik nie mają być przekazywane nieotwarte `CDatabase` obiekt `CRecordset` obiektu w innym wątku.

> [!NOTE]
>  Jeśli konieczne jest posiadanie wielu wątków, manipulowania tego samego obiektu, powinien implementować synchronizacji odpowiednich mechanizmów, takich jak sekcje krytyczne. Należy pamiętać, że niektóre operacje, takie jak `Open`, nie są chronione. Należy się upewnić, że te operacje nie zostaną wywołane jednocześnie z oddzielnych wątkach.

Aby uzyskać więcej informacji o tworzeniu aplikacji wielowątkowych, zobacz [tematy o wielowątkowości](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programowanie (MFC/ATL) dostępu do danych](../../data/data-access-programming-mfc-atl.md)