---
title: COM::PTR, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- com::ptr
- msclr::com::ptr
- msclr.com.ptr
- com.ptr
dev_langs:
- C++
helpviewer_keywords:
- ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c90edb82b9efbd2a265c93ca6a0d6e16b22955fb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397913"
---
# <a name="comptr-class"></a>com::ptr — Klasa

Otoka dla obiektu COM, który może służyć jako członek klasy CLR.  Otoka także automatyzuje zarządzanie okresem istnienia obiektu COM, zwalniając wszystkie należące do firmy odwołania do obiektu, gdy jego destruktor jest wywoływany. Odpowiednikiem [klasa CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Składnia

```
template<class _interface_type>
ref class ptr;
```

#### <a name="parameters"></a>Parametry

*_interface_type*<br/>
Interfejs COM.

## <a name="remarks"></a>Uwagi

Element `com::ptr` można również jako funkcja lokalna zmienna Aby uprościć różne zadania COM i automatyzować zarządzanie okresem istnienia.

A `com::ptr` nie można używać bezpośrednio jako parametru funkcji; Użyj [Tracking Reference Operator](../windows/tracking-reference-operator-cpp-component-extensions.md) lub [Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) zamiast tego.

Element `com::ptr` nie może być bezpośrednio zwracana przez funkcję; zamiast tego użyj dojście.

## <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  Wywoływanie metody publiczne klas wyników w wywołaniach do zamkniętego `IXMLDOMDocument` obiektu.  Próbka tworzy wystąpienie dokumentu XML, wypełnia niektóre prostego formatu XML i jest uproszczone przeszukiwania węzłów w drzewie przeanalizowany do drukowania pliku XML do konsoli.

```
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Zobacz też

[Biblioteka obsługi języka C++](../dotnet/cpp-support-library.md)<br/>
[ptr, składowe](../dotnet/ptr-members.md)