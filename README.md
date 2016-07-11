This sample projects demostrates how resource files (strings.xml, dimens.xml, colors.xml) can be generated by a Gradle script. 
The purpose of this script is to assist the developer by generating the annoying markup files from the supplied name/value pairs:
<code><pre>
task genDimensions(type: dev.bmax.GenDimensTask) {
    dimens = {
        textViewMarginLeft '32dp'
        textViewMarginTop '32dp'
        textViewTextSize '24sp'
    }
}
</pre></code>

Default destination file name and directory can be overriden by a child task:<code><pre>
task genDimensions(type: dev.bmax.GenDimensTask) {
    resDir = '/src/main/res/values-hdpi/'
    fileName = 'dimens_new.xml'
    dimens = {
        // A bunch of dimensions
    }
}
</pre></code>
Note, currently resDir doesn't support nonexistent directories.

In order to use the above custom Gradle tasks, drop GenResTasks.jar into /app/libs and specify the dependency 
in the Gradle script:
<code><pre>
buildscript {
    dependencies {
        classpath files('libs/GenResTasks.jar')
    }
}
</pre></code>

See the full [example] (https://github.com/bmax-moblin/GenResDemo/blob/master/app/autores.gradle)
