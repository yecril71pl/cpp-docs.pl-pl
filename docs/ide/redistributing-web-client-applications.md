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
ms.openlocfilehash: cdde0f8d4edc13e8c1e1a53d8f4393dc7c2dac40
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372473"
---
# <a name="redistributing-web-client-applications"></a>Ponowne dystrybuowanie Aplikacji klienta sieci Web

Jeśli aplikacja używa klas MFC, implementacja formant WebBrowser (na przykład `CHtmlView` lub `CHtmlEditView`), Microsoft Internet Explorer w wersji 4.0 lub nowszy co najmniej musi być co najmniej zainstalowany na komputerze docelowym.

Zainstalowanie najnowszej wersji programu Internet Explorer gwarantuje również, że komputer docelowy ma najnowsze pliki wspólnej kontroli.

Informacje o instalowaniu składników programu Internet Explorer minimalny jest dostępna w następującym artykule bazy wiedzy:

- Q185375, porady: Tworzenie instalacji pojedynczy plik EXE programu Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))

Można znaleźć artykuły bazy wiedzy w bibliotece MSDN lub na [ http://support.microsoft.com ](http://support.microsoft.com).

## <a name="see-also"></a>Zobacz też

[Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)