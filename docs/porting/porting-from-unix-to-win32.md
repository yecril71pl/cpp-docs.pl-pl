---
title: Uruchamianie programów systemu Linux w systemie Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: c91bcf1c9384cd71811d42a14b98dc155626a4d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368468"
---
# <a name="running-linux-programs-on-windows"></a>Uruchamianie programów systemu Linux w systemie Windows

Aby uruchomić program Linux w systemie Windows, masz następujące opcje:

- Uruchom program w stanie niedziałać w podsystemie Windows dla systemu Linux (WSL). W programie WSL program jest wykonywany bezpośrednio na sprzęcie maszyny, a nie na maszynie wirtualnej. WSL umożliwia również bezpośrednie wywołania systemu plików między systemami Windows i Linux, eliminując potrzebę transportu SSL. WSL jest zaprojektowany jako środowisko wiersza polecenia i nie jest zalecane dla aplikacji intensywnie korzystających z grafiki. Aby uzyskać więcej informacji, zobacz [Podsystem systemu Windows dla dokumentacji systemu Linux](/windows/wsl/about).
- Uruchom program w stanie— jest w maszynie wirtualnej systemu Linux lub kontenerze platformy Docker na komputerze lokalnym lub na platformie Azure. Aby uzyskać więcej informacji, zobacz [Maszyny wirtualne](https://azure.microsoft.com/services/virtual-machines/) i [platforma Docker na platformie Azure](https://docs.microsoft.com/azure/docker/).
- Skompiluj program za pomocą gcc lub clang w środowiskach [MinGW](http://MinGW.org/) lub [MinGW-w64,](https://sourceforge.net/p/mingw-w64/wiki2/Home/) które zapewniają warstwę tłumaczenia z Linuksa do wywołań systemowych Windows.
- Skompiluj i uruchom program za pomocą gcc lub clang w środowisku [Cygwin,](https://www.cygwin.com/) który zapewnia pełniejszą środowisko Linuksa w systemie Windows w porównaniu do MinGW lub MinGW-w64.
- Ręcznie przenieść kod z systemu Linux i skompilować dla systemu Windows przy użyciu języka Microsoft C++ (MSVC). Obejmuje to refaktoryzowanie kodu niezależnego od platformy do oddzielnych bibliotek, a następnie ponowne pisanie kodu specyficznego dla systemu Linux, aby użyć kodu specyficznego dla systemu Windows (na przykład interfejsów API Win32 lub DirectX). W przypadku aplikacji wymagających wysokiej wydajności grafiki jest to prawdopodobnie najlepsza opcja.
