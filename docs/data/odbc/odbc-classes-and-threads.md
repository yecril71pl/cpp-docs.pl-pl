---
title: Klasy i wątki ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368689"
---
# <a name="odbc-classes-and-threads"></a>Klasy i wątki ODBC

Począwszy od MFC 4.2, istnieje obsługa wielowątkowe dla klas ODBC MFC. Należy jednak zauważyć, że MFC nie zapewnia obsługę wielowątkową dla klas DAO.

Obsługa wielowątkowa dla klas ODBC ma pewne ograniczenia. Ponieważ te klasy zawijają interfejs API ODBC, są one ograniczone do obsługi wielowątkowej składników, na których są tworzone. Na przykład wiele sterowników ODBC nie są bezpieczne dla wątków; w związku z tym MFC ODBC klasy nie są bezpieczne dla wątków, jeśli używasz ich z jednym z tych sterowników. Należy sprawdzić, czy dany sterownik jest bezpieczny dla wątków.

Podczas tworzenia aplikacji wielowątkowej, należy być bardzo ostrożnym przy użyciu wielu wątków do manipulowania tym samym obiektem. Na przykład przy `CRecordset` użyciu tego samego obiektu w dwóch wątkach może powodować problemy podczas pobierania danych; operacja pobierania w jednym wątku może zastąpić dane pobrane w innym wątku. Bardziej powszechne użycie klas Odbc MFC w oddzielnych wątków jest współużytkować otwarty `CDatabase` obiekt w `CRecordset` wątkach, aby użyć tego samego połączenia ODBC, z oddzielnym obiektem w każdym wątku. Należy zauważyć, że nie należy `CDatabase` przekazywać `CRecordset` nieotwarty obiekt do obiektu w innym wątku.

> [!NOTE]
> Jeśli musisz mieć wiele wątków manipulować tym samym obiektem, należy zaimplementować odpowiednie mechanizmy synchronizacji, takie jak sekcje krytyczne. Należy pamiętać, że niektóre `Open`operacje, takie jak , nie są chronione. Należy upewnić się, że te operacje nie będą wywoływane jednocześnie z oddzielnych wątków.

Aby uzyskać więcej informacji na temat tworzenia aplikacji wielowątkowych, zobacz [Tematy wielowątkowe](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programowanie dostępu do danych (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
