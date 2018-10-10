---
title: Ponowne dystrybuowanie aplikacji klienta sieci Web | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d036f7d46e0db84b8572b26c747947c929972517
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889935"
---
# <a name="redistributing-web-client-applications"></a>Ponowne dystrybuowanie Aplikacji klienta sieci Web

Jeśli aplikacja używa klas MFC, implementacja formant WebBrowser (na przykład `CHtmlView` lub `CHtmlEditView`), Microsoft Internet Explorer w wersji 4.0 lub nowszy co najmniej musi być co najmniej zainstalowany na komputerze docelowym.

Zainstalowanie najnowszej wersji programu Internet Explorer gwarantuje również, że komputer docelowy ma najnowsze pliki wspólnej kontroli. Aby uzyskać więcej informacji, zobacz [instalacji i wdrażania programu Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11).

## <a name="see-also"></a>Zobacz też

[Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)