---
title: Wdrażanie aplikacji Visual C++ do folderu lokalnego dla aplikacji
ms.date: 09/17/2018
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: 33edf4bb736fad62928e11dd0550af6640d411ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786812"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Przewodnik: Wdrażanie aplikacji Visual C++ do folderu lokalnego aplikacji

W tym artykule opisano sposób wdrażania aplikacji w języku Visual C++ kopiować pliki do folderu.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer, który jest zainstalowany program Visual Studio.

- Inny komputer, który nie ma bibliotek języka Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Aby wdrożyć aplikację do folderu lokalnego aplikacji

1. Tworzenie i tworzenie aplikacji MFC, wykonując kroki opisane w [instruktażu: Wdrażanie aplikacji Visual C++ przy użyciu projektu instalacji](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Skopiuj odpowiednie pliki biblioteki MFC i C Run-Time (CRT) z katalogu instalacyjnego programu Visual Studio w \\VC\\redist\\*wersji* folder, a następnie wklej je w folderze \Release\ Projekt MFC. Aby uzyskać więcej informacji na temat innych plików, które mogą wystąpić, aby skopiować zobacz [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

1. Uruchom aplikację MFC na drugim komputerze, który nie ma bibliotek języka Visual C++.

   1. Skopiuj zawartość folderu \Release\ i wklej je w folderze aplikacji na drugim komputerze.

   1. Uruchom aplikację na drugim komputerze.

   Aplikacja zostanie uruchomiona pomyślnie, ponieważ biblioteki Visual C++ nie są dostępne w folderze lokalnego aplikacji.

## <a name="see-also"></a>Zobacz także

[Przykłady wdrożeń](deployment-examples.md)<br/>
