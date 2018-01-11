---
title: "Izolacja wspólnych MFC określa biblioteki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04ed1be46d4c3d7f36bfa501bfc933fbba41e8d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Izolacja biblioteki formantów wspólnych MFC
Biblioteka formantów standardowych teraz jest izolowana w MFC, umożliwiając różnych modułach (na przykład użytkownik bibliotek DLL) Aby użyć innej wersji biblioteki formantów wspólnych przez określenie wersji w manifestach ich.  
  
 Aplikacji MFC (lub kod użytkownika wywołuje przez MFC) wykonywania wywołań do biblioteki formantów wspólnych interfejsów API za pomocą funkcji otoki o nazwie `Afx` *FunctionName*, gdzie *FunctionName* jest nazwą wspólnego Formanty interfejsu API. Te funkcje otoki są zdefiniowane w afxcomctl32.h i afxcomctl32.inl.  
  
 Można użyć [afx_comctl32_if_exists —](reference/run-time-object-model-services.md#afx_comctl32_if_exists) i [afx_comctl32_if_exists2 —](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) makra (zdefiniowanego w afxcomctl32.h), aby ustalić, czy biblioteka formantów standardowych implementuje niektórych interfejsu API zamiast wywoływać metodę [GetProcAddress](../build/getprocaddress.md).  
  
 Z technicznego punktu widzenia wprowadzeniu wywołania wspólnych interfejsów API biblioteki formantów za pomocą klasy otoki `CComCtlWrapper` (zdefiniowany w afxcomctl32.h). `CComCtlWrapper`jest również jest odpowiedzialny za ładowanie i zwalnianie pliku Comctl32.dll. Stan modułu MFC zawiera wskaźnik do wystąpienia `CComCtlWrapper`. Można uzyskiwać dostęp za pomocą klasy otoki `afxComCtlWrapper` makra.  
  
 Należy pamiętać, że wywołania bezpośrednio API formantów wspólnych (bez użycia funkcji otoki MFC) z MFC aplikacji lub użytkownika DLL będzie działać w większości przypadków, ponieważ MFC aplikacji lub użytkownika biblioteki DLL jest powiązany z biblioteki formantów wspólnych go w swoim manifeście wymagane). Jednak kodu MFC musi używać otoki, ponieważ kod MFC mogą być wywoływane z biblioteki DLL użytkowników z różnych wersji biblioteki formantów wspólnych.

