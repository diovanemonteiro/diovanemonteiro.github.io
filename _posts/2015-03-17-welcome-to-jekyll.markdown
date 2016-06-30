---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-03-17 21:48:51
cover: /assets/images/cover.jpg
categories: jekyll update
---

You’ll find this post in your **_posts** directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight html %}
<div class="post-header-container">
    <div class="scrim">
        <header class="post-header">
            <h1 class="title">Markdown Gramma</h1>
            <p class="info">by <strong>Benjamin</strong></p>
        </header>
    </div>
</div>
{% endhighlight %}

{% highlight php %}
<?php
public function actionAutoSave() {
    if (Yii::app()->request->isAjaxRequest) {

        if (isset($_POST['Submissoes'])) {
            $novasubmissao = new Submissoes;
            $novasubmissao->attributes = $_POST['Submissoes'];

            $pathdir = Yii::app()->basePath.'/../uploads/codes/' . $novasubmissao->id_trabalho . '/' . $novasubmissao->id_aluno;

            is_dir($pathdir) || mkdir($pathdir, 0777, true);
            chdir($pathdir);

            $extensao = $novasubmissao->idTrabalho->idlinguagem->extensao;
            $arquivo_fonte   = $pathdir . '/' . $novasubmissao->id_exercicio . $extensao;

            // Escreve no arquivo
            file_put_contents($arquivo_fonte, $novasubmissao->codigo_arquivo);
        }

        echo $novasubmissao->codigo_arquivo;
    }

    return true;
}
?>
{% endhighlight %}

{% highlight ruby %}
def print_hi(name)
    puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

{% highlight ruby %}
var app = angular.module("myApp", ['infinite-scroll']);

/**
 * Editor de Código com a biblioteca Codemirror
 */
var CodeEditor = {
		
	editor: null, 
	timerId: null,
	delay: 1000,
		
	init: function(content, options) {
		
		var settings = $.extend({}, CodeMirror.defaults, options);
		var form = content.find('form')[0];
		var codeMirrorContainer = content.find('.CodeMirror')[0];
		
		if (codeMirrorContainer && codeMirrorContainer.CodeMirror) {
			this.editor = codeMirrorContainer.CodeMirror; 
			this.editor.refresh();
	  	} else {
	    	this.editor = CodeMirror.fromTextArea(content.find('textarea')[0], settings);
			this.editor.on('change', function(cm, e) {
				if (this.timerId != null) {
					clearTimeout(timerId);
				}
				this.timerId = setTimeout(function() {
					this.autoSave(cm);
	            }, this.delay);
			});
	  	}
	}, 
	
	autoSave: function(element, url, update) {
		cm.save();
		$.ajax({
			type: 'post', 
		    url: '/workspace-yii/Codebench/webapp/index.php?r=trabalhos/autosave', 
		    data: $(form).serialize(), 
		    dataType: 'json',
		    beforeSend : function (XMLHttpRequest) {
		    	console.log('ajax before send');
			},
			complete : function(XMLHttpRequest) {
				console.log('ajax complete');
			},
			success : function(data) {
				console.log('ajax success');
			},
			error: function(data) {
				console.log('ajax error');
			}
		});	 	 	
	},
	
	setFullScreen: function(flag) {
		this.editor.setOption('fullScreen', flag);
	},
	
	setMode: function(mode) {
		this.editor.setOption('mode', mode);
	}
	
}
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
