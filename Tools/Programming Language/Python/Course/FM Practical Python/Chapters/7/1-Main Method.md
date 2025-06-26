* For more comprehensive Python Programs, you need to include `main` method.
* The purpose of checking for `main` method is to make sure that the code in your main method is only run when it's executed as a stand alone program $\xrightarrow{Why?}$ Because of how python import system works $\xrightarrow{How?}$ if anyone else import your python program, any code in it execute on import

> [!tip] Wrap things up in your `__main__` method
> it will only run when you run that file specifically, if you import it in other programs, it won't run 