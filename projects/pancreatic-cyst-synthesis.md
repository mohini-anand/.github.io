# 2-D CT → MRI Translation  
*Toward MRI-quality information where only CT is available*

<div class="ct-to-mri-teaser">
  <img src="../images/project-images/ct-to-mri-translation/ct to mri 1.png" alt="Example output from current model">
  <p class="caption">Example output from current model trained for 30 epochs (needs targeted refinement for pancreas)</p>
</div>

## Why it matters
Current state-of-the-art (SOTA) CT→MRI translators rely on whole images and paired data, yet high-quality paired MRI of cyst patients is scarce.  By mastering **unpaired** translation with mask cues, I create synthetic MRI that preserves critical pathology details—laying the groundwork for large-scale cyst classification and treatment-planning studies.

## My Approach

I am building a **mask-conditioned generative model** that turns 2-D abdominal **CT slices containing pancreatic cysts into realistic MRI slices**.  Instead of feeding the network the entire image, I guide it with **organ-specific masks**.  This targeted conditioning helps the generator focus on pancreas texture and cyst boundaries, which standard full-image approaches often blur or distort.


## Where I am now  
- Prototype trained on publicly available abdominal CT/MRI. Needs fine-tuning for within-mask images 
- First qualitative results show clear pancreas texture and cyst boundaries.

## Next milestones
I am on track to publish the preprint and release the code by July, 2025, and aim for a journal submission by August.  

*Detailed methods and evaluation will appear in the forthcoming paper.*
