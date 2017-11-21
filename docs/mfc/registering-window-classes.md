---
title: Rejestrowanie klas okien | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WndProc
dev_langs: C++
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bfcc0cb9459245f4fa6553774ee943555c09d141
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="registering-window-classes"></a>Rejestrowanie klas okien
Okno "klasy" w tradycyjnych programowanie dla systemu Windows definiują właściwości "klasy" (nie klasy C++), z której można utworzyć dowolną liczbę systemu windows. Ten rodzaj klasy jest szablon lub modelu do tworzenia systemu windows.  
  
## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Rejestrowanie klasy okna w tradycyjnych programów dla systemu Windows  
 W programie tradycyjnego dla systemu Windows bez MFC, przetworzyć wszystkie wiadomości do okna jego "procedurę okna" lub "**WndProc**." A **WndProc** jest skojarzony z oknem za pomocą procesu "Rejestrowanie klasy okna". Okno główne jest zarejestrowany w `WinMain` funkcji, ale inne klasy systemu windows może być dowolnym zarejestrowany w aplikacji. Rejestracja jest zależna od struktury, która zawiera wskaźnik do **WndProc** działać wraz z specyfikacje kursora, Pędzel tła i tak dalej. Struktura jest przekazywana jako parametr, oraz nazwę ciągu we wcześniejszym wywołaniu do klasy **RegisterClass** funkcji. W związku z tym klasy rejestracji może być współużytkowane przez wiele okien.  
  
## <a name="window-class-registration-in-mfc-programs"></a>Rejestrowanie klasy okna w programach MFC  
 Natomiast większość działań rejestracja klasy okna odbywa się automatycznie w programu MFC framework. Jeśli używasz MFC zwykle wyprowadzenia klasy okna języka C++ z istniejącej klasy biblioteki dziedziczenia klasy przy użyciu normalnego składni języka C++. Platforma nadal korzysta z tradycyjnego "rejestracji klasy" który zawiera kilka z nich standardowe, rejestrowana w razie potrzeby. Możesz zarejestrować dodatkowych rejestracji klasy przez wywołanie metody [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) funkcji globalnej, a następnie przekazywanie zarejestrowanych klasy **Utwórz** funkcji członkowskiej klasy `CWnd`. Zgodnie z opisem w tym miejscu tradycyjne "rejestracji class" w systemie Windows jest nie należy mylić z klasy C++.  
  
 Aby uzyskać więcej informacji, zobacz [techniczne Uwaga 1](../mfc/tn001-window-class-registration.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie okien](../mfc/creating-windows.md)

