---
title: InitInstance, Skladowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d026665a48d038092031bf4b632b7ef676124196
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198178"
---
# <a name="initinstance-member-function"></a>InitInstance — Funkcja członkowska
System operacyjny Windows umożliwia uruchamianie więcej niż jedną kopię lub "wystąpienie" tej samej aplikacji. `WinMain` wywołania [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) za każdym razem, gdy uruchamia nowe wystąpienie aplikacji.  
  
 Standardowa `InitInstance` implementacji tworzone przez Kreatora aplikacji MFC wykonuje następujące zadania:  
  
-   Jako jej centralnej akcja tworzy szablonów dokumentów, które z kolei tworzyć dokumentów, widoków i okien ramowych. Aby uzyskać opis tego procesu, zobacz [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md).  
  
-   Ładuje opcji standardowego pliku z pliku ini lub rejestru Windows, łącznie z nazwami ostatnio używanych plików.  
  
-   Rejestruje jedną lub więcej szablonów dokumentów.  
  
-   Aplikacja MDI tworzy się w oknie głównym ramki.  
  
-   Przetwarza wiersza polecenia, aby otworzyć dokument, określone w wierszu polecenia lub, aby otworzyć nowy pusty dokument.  
  
 Można dodawać kodu inicjowania lub modyfikować kod napisany przez kreatora.  
  
> [!NOTE]
>  Aplikacji MFC muszą być zainicjowane w formacie komórek wielowątkowych pojedynczego (STA). Jeśli wywołasz [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) w swojej `InitInstance` zastąpienia, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED). Aby uzyskać więcej informacji, zobacz PRB: Aplikacja MFC przestaje odpowiadać podczas inicjowania aplikacji jako wielowątkowe apartamentu (828643) na [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
