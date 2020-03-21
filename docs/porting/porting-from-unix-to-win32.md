---
title: Uruchamianie programów systemu Linux w systemie Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 1c1807cee07db479a91f45e21434b3ba13be2ab6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076901"
---
# <a name="running-linux-programs-on-windows"></a>Uruchamianie programów systemu Linux w systemie Windows

Aby uruchomić program systemu Linux w systemie Windows, dostępne są następujące opcje:

- Uruchom program w postaci, w której znajduje się podsystem Windows dla systemu Linux (WSL). W programie WSL program jest wykonywany bezpośrednio na sprzęcie komputera, a nie na maszynie wirtualnej. WSL również włącza bezpośrednie wywołania systemu plików między systemami Windows i Linux, eliminując konieczność transportu SSL. WSL jest zaprojektowana jako środowisko wiersza polecenia i nie jest zalecane w przypadku aplikacji intensywnie korzystających z grafiki. Aby uzyskać więcej informacji, zobacz temat [podsystem Windows dla systemu Linux](/windows/wsl/about).
- Uruchom program w taki sam sposób, jak w przypadku maszyny wirtualnej z systemem Linux lub kontenera Docker, na komputerze lokalnym lub na platformie Azure. Aby uzyskać więcej informacji, zobacz [Virtual Machines](https://azure.microsoft.com/services/virtual-machines/) i [Docker na platformie Azure](https://docs.microsoft.com/azure/docker/).
- Skompiluj program przy użyciu usługi Microsoft w zatoce lub Clang w środowiskach [MinGW](http://MinGW.org/) lub [MinGW-W64](https://MinGW-w64.org/doku.php) , które zapewniają warstwę translacji z wywołań systemu Linux do systemu Windows.
- Kompiluj i uruchamiaj program za pomocą usługi Microsoft w zatoce lub Clang w środowisku [Cygwin](https://www.cygwin.com/) , które zapewnia pełniejsze środowisko systemu Linux w systemie Windows w porównaniu do MinGW lub MinGW-W64.
- Ręcznie przeportować kod z systemu Linux i Kompiluj dla Windows C++ przy użyciu programu Microsoft (MSVC). Obejmuje to refaktoryzację kodu niezależnego od platformy do oddzielnych bibliotek, a następnie ponowne zapisanie kodu specyficznego dla systemu Linux w celu użycia kodu specyficznego dla Windows (na przykład interfejsów API Win32 lub DirectX). W przypadku aplikacji, które wymagają grafiki o wysokiej wydajności, jest to prawdopodobnie najlepsza opcja.
