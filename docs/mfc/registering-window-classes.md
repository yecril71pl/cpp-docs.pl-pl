---
title: Rejestrowanie klas okien
ms.date: 11/04/2016
f1_keywords:
- WndProc
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
ms.openlocfilehash: 7c459b909a60fff2b7aeded9ea8d79a39ced24e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309086"
---
# <a name="registering-window-classes"></a>Rejestrowanie klas okien

Okno "klasy" w tradycyjnego programowania Windows definiują właściwości "class" (nie klasy języka C++), z której można utworzyć dowolną liczbę systemu windows. Tego rodzaju klasy jest szablon lub modelu tworzenia systemu windows.

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Rejestrowanie klasy okna w tradycyjnych programów dla Windows

W tradycyjnych program Windows bez MFC, są przetwarzane wszystkie komunikaty do okna w jego "procedurę okna" lub "`WndProc`." Element `WndProc` jest skojarzony z oknem przy użyciu procesu "Rejestrowanie klasy okna". Okno główne jest zarejestrowany w `WinMain` funkcji, ale inne klasy systemu windows można rejestrować dowolne miejsce w aplikacji. Rejestracja jest zależny od struktury, która zawiera wskaźnik do `WndProc` funkcji wraz z specyfikacją kursora, Pędzel tła i tak dalej. Struktura jest przekazywany jako parametr, wraz z nazwą ciągu klasy, w wywołaniu `RegisterClass` funkcji. W związku z tym klasa rejestracji może być współużytkowane przez wiele okien.

## <a name="window-class-registration-in-mfc-programs"></a>Rejestrowanie klasy okna dla programów MFC

Z kolei większość działań rejestracji klasy okna odbywa się automatycznie w programu MFC framework. Jeśli używasz MFC zazwyczaj pochodzić klasy okna języka C++ z istniejącej klasy biblioteki przy użyciu normalnych składni języka C++ do obsługi dziedziczenia klasy. Struktura nadal korzysta z tradycyjnych "klasy rejestracji" który zawiera kilka z nich standardowe, rejestrowana w razie. Możesz zarejestrować dodatkowe rejestracji klasy przez wywołanie metody [afxregisterwndclass —](../mfc/reference/application-information-and-management.md#afxregisterwndclass) funkcja globalna, a następnie przekazywanie zarejestrowanych klasy `Create` funkcji składowej typu `CWnd`. Zgodnie z opisem w tym miejscu tradycyjne "class rejestracji" w Windows jest nie należy mylić z klasy języka C++.

Aby uzyskać więcej informacji, zobacz [techniczne Uwaga 1](../mfc/tn001-window-class-registration.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie okien](../mfc/creating-windows.md)
