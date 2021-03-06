Welcome to Free Pascal Testing Framework (FPTest)
=================================================

This is a fork of the DUnit2 project, and further adapted for the use
with the Free Pascal Compiler and fpGUI Toolkit. The original code was
created by the late Peter McNab. He single handedly added some excellent
features to DUnit2 and used the extensive test suite from tiOPF as his
playground.

As of July 2009, I (Graeme Geldenhuys) decided to continue Peter's work
on DUnit2, but renamed the project to prevent confusion with the Delphi
based DUnit2 project hosted on SourceForge [which is a continuation of
Peter's work too]. I applied some of my own ideas listed below:

 * No need for Delphi.NET support. The product doesn't exist anymore
   and .NET has its own testing framework anyway, called NUnit.
 * Must work with the Free Pascal Compiler (FPC).
 * Don't need Delphi support, because FPC is a excellent compiler.
 * With FPC support comes the idea that it must be cross-platform
   friendly as well.
 * Due to the previous item, removing the idea of writing to the Windows
   Registry is a logical step. Using something like INI, XML or JSON config
   files will do a great job, are easy to edit, and works for all OSes.

Unit tests comprise of classes derived from TTestCase, each containing one
or more published test procedures as shown in the example below. TTestCase
is now an interfaced object.

type
  TTestMyComms = class(TTestCase)
  published
    procedure VerifyThatThereIsAnUnAssignedCommPort;
    procedure VerifyThatTheCommPortOpens;
    procedure VerifyThatTheCommPortCloses;
  end;

Through the magic of RTTI, FPTest is able to execute the published test
procedures in an orderly fashion. Code written into test methods
performs tests on user's code, and calls one or more Check() procedures
to signal pass or fail to the test framework.

For more information about FPTest, have a look at the various documents
in the 'docs' directory.


