---
title: Wdrażanie aplikacji Visual C++ do folderu lokalnego dla aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/17/2018
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
ms.openlocfilehash: f749a288ac08adfb5df5291ce3dd92b95c2301e8
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234245"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Wskazówki: wdrażanie aplikacji Visual C++ do folderu lokalnego aplikacji

W tym artykule opisano sposób wdrażania aplikacji w języku Visual C++ kopiować pliki do folderu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- Komputer, który jest zainstalowany program Visual Studio.  
  
- Inny komputer, który nie ma bibliotek języka Visual C++.  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Aby wdrożyć aplikację do folderu lokalnego aplikacji  
  
1. Utworzyć i skompilować aplikację MFC, wykonując kroki opisane w [wskazówki: Wdrażanie Visual C++ Application By Using projektu Instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
1. Skopiuj odpowiednie pliki biblioteki MFC i C Run-Time (CRT) z katalogu instalacyjnego programu Visual Studio w \\VC\\redist\\*wersji* folder, a następnie wklej je w folderze \Release\ Projekt MFC. Aby uzyskać więcej informacji na temat innych plików, które mogą wystąpić, aby skopiować zobacz [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).  
  
1. Uruchom aplikację MFC na drugim komputerze, który nie ma bibliotek języka Visual C++.  
  
   1. Skopiuj zawartość folderu \Release\ i wklej je w folderze aplikacji na drugim komputerze.  
  
   1. Uruchom aplikację na drugim komputerze.  
  
   Aplikacja zostanie uruchomiona pomyślnie, ponieważ biblioteki Visual C++ nie są dostępne w folderze lokalnego aplikacji.  
  
## <a name="see-also"></a>Zobacz też  

[Przykłady wdrożeń](deployment-examples.md)<br/>
