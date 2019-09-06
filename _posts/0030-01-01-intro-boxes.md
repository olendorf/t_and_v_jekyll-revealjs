

<div class="studio template background">
    <div class="screen one">
        <h2>Screen 1</h2>
        <p> There is some, hopefully useful, documentation included in this demo.
            Read through them to get started.</o>
    </div>
    <div class="screen two">
        <h2>Screen 2</h2>
        <p> There are ten projectors you can spread content across</p>
        <p> Testing multiple lines here </p>
        <ul>
            <li>You can also use fragments</li><fragment/>
            <li>To reveal content little</li><fragment/>
            <li>..little</li><fragment/>
        <ul>
    </div>
    <div class="screen three">
        <h2>Screen 3</h2>
        <p>These boxes are a guide to help you see the recommended
           positioning for content</p>
        <p>You use the <code>template</code> class in the HTML to turn the boxes
           on and off</p>
        <pre>
            <code>
<!-- All this gets displayed as code -->
<div class="studio template background">
 <div class="screen one">
  <h2>Screen 1</h2>
   # ...
   # All your code here
   # ...
 </div>
</div>
<!-- From now on it behaves as normal -->
            </code>
        </pre>
    </div>
    </fragment>
    <div class="screen four">
        ## Screen 4
        We can also use **Markdown** to add content.
```markdown
<div class="screen four">
 ## Screen 4
 We can also use **Markdown** to add content.
</div>
```
    </div>
    <div class="screen five">
        <h2>Screen 5</h2>
        <div class="img">
        <p>Sometimes you want a pretty picture</p>
        <img src="assets/img/inga.png" height=500>
        </div>
    </div>
    <div class="screen six">
        <h2>Screen 6</h2>
        <HR>
        <h3>10 Screen Template</h3>
        <p> This template has separate divisions for each projector</p>
    </div>
    <div class="screen seven">
        <h2>Screen 7</h2>
        <p> Using markdown to generate the code.</p>
        
```ruby
# The methods return true if the user's role is equal to or less than the
# rank of the can_be method. So if a user is an admin, #can_be_user? or
# #can_be_admin? would return true, but
# can_be_owner? would return false.
User.roles.each do |role_name, value|
 define_method("can_be_#{role_name}?") do
  value <= self.class.roles[role]
 end
end
```
        <p> <strong>Only use single spaces to indent though!</strong></p>
    </div>
    <div class="screen eight">
        <h2>Screen 8</h2>
        <p>Sometimes you might want to leave a screen empty. You still need to leave the place holder there.
        <pre>
            <code>
<div class="screen eight">
 # This is the code for screen nine, but without this comment,
</div>
            </code>
        </pre>
        <h3> Thats screen nine! -----> </h3>
    </div>
    <div class="screen nine">
    </div>
    <div class="screen ten">
        <h2>Screen 10</h2>
        <p><strong>Two images side by side</strong></p>
        <div class="row">
            <div class="two column left">
                <img src="assets/img/inga.png">
            </div>
            <div class="two column right">
                <img src="assets/img/gd.png">
            </div><fragment/>
        </div>
    </div>
</div>

---

<div class="studio">
    <div class="screen panoramic">
      <div style="background-color: black; width: 1200px; display: inline-block; margin: 350px auto">
        <h1> This slide is on the same document as the previous one.</h1>
      </div>
</div>

--

<div class="studio">
    <div class="screen panoramic">
      <div style="background-color: black; width: 1200px; display: inline-block; margin: 350px auto">
        <h1> You went down to get here!</h1>
      </div>
</div>


