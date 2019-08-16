---
title: Błąd krytyczny C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 33c17a3099f4aed99cc26579d0e65c4a350b4268
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501090"
---
# <a name="fatal-error-c1510"></a>Błąd krytyczny C1510

Nie można otworzyć zasobu języka językowego clui. dll.

Kompilator nie może załadować biblioteki DLL zasobów języka.

Istnieją dwie typowe przyczyny tego problemu. W przypadku korzystania z 32-bitowego kompilatora i narzędzi, ten błąd może pojawić się w przypadku dużych projektów, które używają więcej niż 2 GB pamięci podczas łączenia. Możliwym rozwiązaniem w 64-bitowych systemach Windows jest użycie z 64-bitowym kompilatorem natywnym lub krzyżowym oraz narzędzi do generowania kodu. Umożliwia to wykorzystanie większej ilości miejsca dostępnego w pamięci dla aplikacji 64-bitowych. Jeśli musisz użyć 32-bitowego kompilatora, ponieważ Pracujesz w systemie 32-bitowym, w niektórych przypadkach można zwiększyć ilość pamięci dostępnej dla konsolidatora do WŁĄCZONĄ. Aby uzyskać więcej informacji, [Zobacz 4-gigabajtowe dostrajanie: Bcdedit i Boot. ini](/windows/win32/memory/4-gigabyte-tuning) oraz polecenie [bcdedit/set IncreaseUserVa](/windows-hardware/drivers/devtest/bcdedit--set) .

Inną typową przyczyną jest uszkodzenie lub niepełna instalacja programu Visual Studio. W takim przypadku ponownie uruchom Instalatora, aby naprawić lub ponownie zainstalować program Visual Studio.
