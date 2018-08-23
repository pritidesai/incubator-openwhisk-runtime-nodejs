---
title: Node.js Runtime
description: Start here to learn how to use Node.js Runtime
---

<main id="doc">
    <div class="content">
        <a class="indexable" id="nodejs"></a>
        <h4>Apache OpenWhisk Runtime for Node.js</h4>
        <p>The basics of creating OpenWhisk action is explained in core OpenWhisk repo under
        [OpenWhisk Actions](https://github.com/apache/incubator-openwhisk/blob/master/docs/actions.md#the-basics).
        The following sections walks you through creating and invoking a simple JavaScript action such as `hello world`.
        Then add parameters to an action and invoke that action with parameters, followed by setting default parameters and invoking action.
        Finally, demonstrate how to bundle multiple JavaScript files and third party modules.</p>
        <a class="indexable" id="nodejs-actions"></a>
        <h5>Creating and Invoking NodeJS actions</h5>
        <p>
            Let's look at how to write a sample hello world action in NodeJS. You can visit
            <a href="https://github.com/apache/incubator-openwhisk/blob/master/docs/actions-node.md#creating-and-invoking-javascript-actions">Creating and Invoking NodeJS actions</a>
            page for further details.
        </p>
        <p>
            <strong>Note:</strong> We will be using <i>wsk</i> CLI in this section. If you don't have it installed and configured,
            please refer to the section on <a href="#wsk-cli">Configure the wsk CLI</a> to configure it.
        </p>
        <ol>
            <li style="list-style-type: decimal">
                Create a JavaScript file named <i>hello.js</i> with the following content:
                <div class="terminal">
<pre><code class="javascript">
function main() {
    return { payload: 'Hello world' };
}
</code></pre>
                        </div>
                    </li>
                    <li style="list-style-type: decimal">
                        Create an action using <i>hello.js</i> with <i>wsk</i> CLI:
                        <div class="terminal">
<pre><code>$ wsk action create helloJS hello.js</code></pre>
                        </div>
                        <div class="terminal">
                            <pre>ok: created action helloJS</pre>
                        </div>
                    </li>
                    <li style="list-style-type: decimal">
                        Invoke the <i>helloJS</i> action as a blocking activation:
                        <div class="terminal">
{% highlight bash %}$ wsk action invoke helloJS --blocking{% endhighlight %}
                        </div>
                        <div class="terminal">
{% highlight yaml %}
{
  "result": {
      "payload": "Hello world"
    },
    "status": "success",
    "success": true
}{% endhighlight %}
                        </div>
                    </li>
                    <li style="list-style-type: decimal">
                        Deploy using <i>wskdeploy</i>:
                        <p>
                            <strong>Note:</strong> We will be using <i>wskdeploy</i> in this section. If you don't have the binary,
                            please refer to the section on <a href="#wskdeploy">Whisk Deploy</a> to download it.
                        </p>
                        <ol>
                            <li>
                                Create <i>manifest.yaml</i> with the following YAML content:
                                <div class="terminal">
{% highlight yaml linenos %}
{% include code/manifest-for-helloJS-1.yaml %}
{% endhighlight %}
                                </div>
                                Or
                                <p></p>
                                <div class="terminal">
        {% highlight yaml linenos %}
        {% include code/manifest-for-helloJS-2.yaml %}
        {% endhighlight %}
                                </div>
                            </li>
                            <li>
                                Run deployment with <i>wskdeploy</i>:
                                <div class="terminal">
{% highlight bash %}$ wskdeploy -m manifest.yaml{% endhighlight %}
                                </div>
                            </li>
                        </ol>
                    </li>
                </ol>
                <a class="indexable" id="nodejs-runtime"></a>
                <h5>OpenWhisk Runtime for NodeJS</h5>
                <p>
                    OpenWhisk supports <strong>Node.js 6</strong> and <strong>Node.js 8</strong> runtimes where Node.js 6 being default pick by wsk CLI and Whisk Deploy.
                    If you wish to learn more about NodeJS runtime along with
                    the libraries that are supported or "built-in" by default, please visit
                    <a href="https://github.com/apache/incubator-openwhisk-runtime-nodejs/blob/master/README.md">NodeJS Runtime GitHub Repository</a>.
                </p>
                <a class="indexable" id="nodejs-additional-resources"></a>
                <h5>Additional Resources</h5>
                <ul>
                    <li><a href="https://medium.com/openwhisk/debugging-node-js-openwhisk-actions-3da3303e6741">Debugging Node.js OpenWhisk Actions</li>
                    <li><a href="https://medium.com/openwhisk/updates-to-openwhisk-node-js-actions-ed5556cd5ae9">Updates to OpenWhisk Node.js actions</a></li>
                    <li><a href="https://medium.com/openwhisk/integrating-openwhisk-with-your-node-application-d489b8a20102">Integrating OpenWhisk with Your Node Applications</a></li>
                </ul>
            </div>
        </main>