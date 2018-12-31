.. title: LZMA SDK (Software Development Kit)
.. slug: sdk
.. date: 2018-12-30 18:50:30 UTC+02:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

LZMA SDK (Software Development Kit)
===================================

Das **LZMA SDK** bietet eine Dokumentation, Beispiele, Headerdateien,
Bibliotheken und Werkzeuge, um Anwendungen zu entwickeln, die die
**LZMA**-Kompression verwenden.

+----------------------------------------------------------+-------+------------+---------+------------------------------------+
| Link                                                     | Größe | Datum      | Version | Beschreibung                       |
+==========================================================+=======+============+=========+====================================+
| `Download <https://7-zip.org/a/lzma1806.7z>`__           |  1 MB | 30.12.2018 | 18.06   | | LZMA SDK                         |
+----------------------------------------------------------+-------+------------+---------+ | C, C++, C#, Java                 |
| `Download <https://7-zip.org/a/lzma1801.7z>`__           |  1 MB | 28.01.2018 | 18.01   | | x86/x64-Binärdateien für Windows |
+----------------------------------------------------------+-------+------------+---------+                                    |
| `Download <https://7-zip.org/a/lzma1604.7z>`__           |  1 MB | 04.10.2016 | 16.04   |                                    |
+----------------------------------------------------------+-------+------------+---------+------------------------------------+
| `Download <https://7-zip.org/a/lzma-specification.7z>`__ | 12 KB | 14.06.2015 |         | LZMA-Spezifikation (Entwurf)       |
+----------------------------------------------------------+-------+------------+---------+------------------------------------+

**Was ist neu:**

-  **18.06:** Einige Geschwindigkeitsoptimierungen im LZMA/LZMA2-Code.
-  **18.05:** Einige Geschwindigkeitsoptimierungen im LZMA/LZMA2-Code.
-  **18.01:** Einige Änderungen im LZMA2/xz-Multithreading-Code für Kompression. Einige Fehler wurden behoben.
-  **9.35:** AES-Code und SFX-Module wurden in das SDK integriert.
-  **9.20:** Neues kleines SFX-Modul für Installationsroutinen.
-  **9.11:** Unterstützung für PPMd.
-  **9.04:** Unterstützung für LZMA2 und XZ.
-  **4.62:** Einige Fehler wurden behoben. LZMA SDK wird Public Domain.

**LZMA / LZMA2** sind die voreingestellte und allgemeine Kompressionsmethoden des :doc:`7z-Formates <7z>` in **7-Zip**. **LZMA** bietet eine hohe Kompressionsrate und sehr schnelle Dekompression, so dass es sich sehr gut für eingebettete Anwendungen eignet. Beispielsweise kann es zur ROM (Firmware)-Kompression benutzt werden.

**LZMA SDK** beinhaltet:

-  **C++**-Quelltext des **LZMA**-Encoder und -Decoder
-  **C++**-Quelltext für **.7z**-Kompression und -Dekompression (reduzierte Version)
-  **ANSI-C**-kompatibler Quelltext für **LZMA/LZMA2/XZ**-Kompression und -Dekompression
-  **ANSI-C**-kompatibler Quelltext für **7z**-Dekompression mit Beispielen
-  **C#**-Quelltext für **LZMA**-Kompression und -Dekompression
-  **Java**-Quelltext für **LZMA**-Kompression und -Dekompression
-  **lzma.exe** zur Kompression und Dekompression von .lzma
-  **7zr.exe** zur Arbeit mit 7z-Archiven (reduzierte Version der 7z.exe von 7-Zip)
-  **SFX-Module** zur Erstellung von selbstextrahierenden Paketen und Installern

Die Quelltexte in **ANSI-C** und **C++** des LZMA SDK sind Teile des Quelltextes von 7-Zip.

Eigenschaften von **LZMA**:

-  Kompressionsgeschwindigkeit: 3 MB/s mit 3 GHz Dual-Core CPU.
-  Dekompressionsgeschwindigkeit:

   -  20–50 MB/s mit moderner 2 GHz CPU (Intel, AMD).
   -  5–10 MB/s mit einfacher 1 GHz RISC CPU (ARM, MIPS, PowerPC)

-  Nur wenig Arbeitsspeicher zum Dekomprimieren nötig: 8–32 KB + Wörterbuchgröße
-  Geringe Größe beim Entpacken: 2–8 KB (abhängig von Geschwindigkeitsoptimierungen)

Der **LZMA**-Dekoder nutzt nur CPU-Integerbefehle und kann für jede
moderne 32bit-CPU implementiert werden (auf 16bit-CPU mit Abstrichen).

Lizenz
------

**LZMA SDK** steht unter der **Public Domain.**

Jeder darf den originalen LZMA-SDK-Code kopieren, ändern, veröffentlichen, nutzen, kompilieren, verkaufen oder verteilen, sowohl als Quelltext als auch als kompilierte Binärdatei, für jeden Zweck, kommerziell oder nichtkommerziell, unter allen Umständen.

LZMA Links
----------

-  `LZMA bei Wikipedia <https://de.wikipedia.org/wiki/Lempel-Ziv-Markow-Algorithmus>`__
-  `LZMA-Benchmarkergebnisse für verschiedene CPUs <https://www.7-cpu.com/>`__
-  `XZ Utils / LZMA Utils <https://tukaani.org/xz/>`__
-  `Portierung von LZMA SDK auf JAVA, erstellt von einem unabhängigen Entwickler <https://sourceforge.net/projects/p7zip/>`__
-  `Portierung von LZMA SDK auf Pascal (Delphi, Kylix and Freepascal) <https://www.birtles.org.uk/programming/>`__
-  `PyLZMA: Python-Bindings für LZMA <https://www.joachim-bauch.de/projects/pylzma/>`__
-  `LZMA Streams in Java <http://contrapunctus.net/league/haques/lzmajio/>`__
-  `Zip-Ada: LZMA auf Ada <http://unzip-ada.sourceforge.net/>`__
