---
title: Wdrażanie aplikacji Visual C++ do folderu lokalnego dla aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04b97ebffe5e44c4743df3b67987f0d27bba8a8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426279"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Wskazówki: wdrażanie aplikacji Visual C++ do folderu lokalnego aplikacji

W tym artykule opisano sposób wdrażania aplikacji w języku Visual C++ kopiować pliki do folderu.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer, który jest zainstalowany program Visual Studio.

- Inny komputer, który nie ma bibliotek języka Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Aby wdrożyć aplikację do folderu lokalnego aplikacji

1. Utworzyć i skompilować aplikację MFC, wykonując kroki opisane w [wskazówki: Wdrażanie Visual C++ Application By Using projektu Instalatora](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Skopiuj odpowiednie pliki biblioteki MFC i C Run-Time (CRT) — na przykład dla x86 platformy i obsługa systemu Unicode, kopia pliku mfc100u.dll i rozdystrybuować msvcr100.dll z 10.0\VC\redist\x86\—and programu Visual Studio \Program Files\Microsoft następnie wklej je w folderze \Release\ Projekt MFC. Aby uzyskać więcej informacji na temat innych plików, które mogą wystąpić, aby skopiować zobacz [Determining Which DLLs to Redistribute](../ide/determining-which-dlls-to-redistribute.md).

1. Uruchom aplikację MFC na drugim komputerze, który nie ma bibliotek języka Visual C++.

   1.  Skopiuj zawartość folderu \Release\ i wklej je w folderze aplikacji na drugim komputerze.

   1.  Uruchom aplikację na drugim komputerze.

   Aplikacja zostanie uruchomiona pomyślnie, ponieważ biblioteki Visual C++ nie są dostępne w folderze lokalnego aplikacji.

## <a name="see-also"></a>Zobacz też

[Przykłady wdrożeń](../ide/deployment-examples.md)