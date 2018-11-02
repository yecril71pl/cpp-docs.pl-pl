---
title: Ponowne dystrybuowanie Aplikacji klienta sieci Web
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
ms.openlocfilehash: 37ff666493ada7dada19f5731e6581603d3cb57e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512423"
---
# <a name="redistributing-web-client-applications"></a>Ponowne dystrybuowanie Aplikacji klienta sieci Web

Jeśli aplikacja używa klas MFC, implementacja formant WebBrowser (na przykład `CHtmlView` lub `CHtmlEditView`), Microsoft Internet Explorer w wersji 4.0 lub nowszy co najmniej musi być co najmniej zainstalowany na komputerze docelowym.

Zainstalowanie najnowszej wersji programu Internet Explorer gwarantuje również, że komputer docelowy ma najnowsze pliki wspólnej kontroli. Aby uzyskać więcej informacji, zobacz [instalacji i wdrażania programu Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11).

## <a name="see-also"></a>Zobacz też

[Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)